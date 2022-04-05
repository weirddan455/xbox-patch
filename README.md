# Linux kernel patch for Xbox One S Bluetooth Controller

This patch does some button remapping for the driver used via bluetooth to match the mapping when this controller is used via USB.

## Building

If you are compiling your own kernel, you can simply use the xbox.patch file from inside the kernel source tree like

```
cd /path/to/kernel-src
patch -Np1 < /path/to/this/repo/xbox.patch
```

I've also provided the module-build directory which contains the full source to the hid-microsoft driver meant to be compiled as a module using your existing kernel (no full kernel recompilation required).

To do this, you will need the kernel headers installed.  If using a distro kernel, this should just be a package you can install (ex. linux-headers on Arch).  You'll also need gcc and make installed.  Then, input these commands to build and use the new module.

```
cd module-build
make
sudo rmmod hid-microsoft
sudo insmod hid-microsoft.ko
```
