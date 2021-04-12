#!/bin/bash

set -euo pipefail

# Install rustup

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs > rustup-init.sh
chmod +x rustup-init.sh
./rustup-init.sh -y --default-toolchain nightly-2021-04-10 --profile minimal
rm rustup-init.sh
export PATH="~/.cargo/bin:$PATH"

# Install node

wget https://nodejs.org/dist/v14.16.1/node-v14.16.1-linux-x64.tar.gz
tar zvxf node-v14.16.1-linux-x64.tar.gz
export PATH="~/node-v14.16.1-linux-x64/bin:$PATH"

# Install yarn

wget https://nightly.yarnpkg.com/yarn-v1.23.0-20210103.1434.tar.gz
tar zvxf yarn-v1.23.0-20210103.1434.tar.gz
export PATH="~/yarn-v1.23.0-20210103.1434/bin:$PATH"

# Install sqlite3

mkdir sqlite
wget -O sqlite/sqlite3 https://github.com/boramalper/sqlite3-x64/releases/download/3240000--2018-08-05T15.32.14Z/sqlite3
chmod +x sqlite/sqlite3
export PATH="~/sqlite:$PATH"

# Build frontend

pushd app
yarn
yarn build
popd

# Build backend

cargo build --release
