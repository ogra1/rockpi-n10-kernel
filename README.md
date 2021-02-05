# rockpi-n10-kernel

Ubuntu Core 20 kernel snap for the RockPi N10 found at https://github.com/radxa/kernel.git 
in the rk3399pro-toybrick-stable branch using the rockchip_linux_defconfig configuration.

The build applies the apparmor 4.4 patch set from:
https://gitlab.com/apparmor/apparmor/-/tree/master/kernel-patches/4.4
and an Ubuntu Core set of extra configuration options.

## building

This snap is designed for cross building, run the instructions below on a PC 

- install lxd and create a focal (20.04) lxd container

    ```
    $ sudo snap install lxd
    $ sudo lxd init --auto
    $ sudo lxc launch ubuntu:20.04 focal
    ```

- enter the container and install snapcraft

    ```
    $ sudo lxc shell focal
    # snap install snapcraft --classic
    ```

- clone this branch and build it

    ```
    # git clone https://github.com/ogra1/rockpi-n10-kernel.git
    # cd rockpi-n10-kernel
    # snapcraft --destructive-mode --target-arch=arm64
    ...
    Snapped rockpi-n10-kernel_4.4.167-16-rockchip_arm64.snap
    # exit
    $
    ```

- pull the file from the container

    ```
    $ lxc file pull focal/root/rockpi-n10-kernel/rockpi-n10-kernel_4.4.167-16-rockchip_arm64.snap .
    $
    ```

now you can use this snap, a gadget snap for the N10 and a model assertion to build an UC20 image
