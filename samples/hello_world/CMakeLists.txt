# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

add_compile_options( -flto )
add_link_options( -flto )
# fix1: undefined reference to `memcpy'
add_link_options( -fno-ipa-sra )
add_link_options( -ffunction-sections -fdata-sections )


find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(hello_world)

target_sources(app PRIVATE src/main.c)
