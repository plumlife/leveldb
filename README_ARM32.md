# Welcome!
This is Plum's fork of LevelDB to support building for arbitrary Linux OS's on the ARM. The support is very simple, it's a minor addition to the `build_detect_platform` script that will also require a few pre-requisite environment variables before you `make all`.

Notably, you should export the `PATH` to your cross-compiled toolchain's bin directory and also override the standard GNU compiler tools like this:
```
export PATH="/root/x-tools/arm-plum-linux-gnueabi/bin:$PATH"
export CC="arm-plum-linux-gnueabi-gcc"
export CXX="arm-plum-linux-gnueabi-g++"
export AR="arm-plum-linux-gnueabi-ar"
export RANLIB="arm-plum-linux-gnueabi-ranlib"
export TARGET_OS="OS_LINUX_ARM_CROSSCOMPILE"
```

Also note the `TARGET_OS` variable, the value for that variable is a generic Linux for ARM target.

A simple `make all` should build LevelDB. If you want to run the tests, you'll need to compile all of the tests then copy them to your ARM environment and run them there. Of note, I have done this and *all tests have passed*.
