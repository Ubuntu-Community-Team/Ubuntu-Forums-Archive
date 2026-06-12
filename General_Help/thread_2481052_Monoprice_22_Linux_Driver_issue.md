---
title: "Monoprice 22 Linux Driver issue"
date: 2022-11-17
forum: General Help
---

### Post by MZ250Supa5 on 2022-11-17
I'm usually able to install this driver with no issues - at least I was with 16.04 to 20.04 but now with the change to 22.04 all sorts of issues have come to the fore. Not least of which is the refusal of the system to install this necessary driver so that I can use my pricey pen monitor on Ubuntu.

When installing the driver I follow the directions for both make and make install, (and yes, I do prefix with sudo on the second command) but I get the following error report:

```
modprobe: ERROR: could not insert 'mono_22': Exec format error
make: *** [Makefile:28: install] Error 1
```


The full process output is as follows:

```
padi@moron:~$ cd Monoprice_22_linux_kernel_module-master/
padi@moron:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/5.15.0-53-generic/build M=/home/padi/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-53-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-53-generic'
padi@moron:~/Monoprice_22_linux_kernel_module-master$ sudo make install
[sudo] password for padi: 
cp ./mono_22.ko /lib/modules/5.15.0-53-generic/kernel/drivers/input/tablet/
echo mono_22 >> /etc/modules
depmod
cp ./load_mono_22.sh /usr/local/bin
cp ./detach_usbhid /usr/local/bin
cp ./load_mono_22.rules /etc/udev/rules.d
/bin/udevadm control --reload
modprobe mono_22
modprobe: ERROR: could not insert 'mono_22': Exec format error
make: *** [Makefile:28: install] Error 1
padi@moron:~/Monoprice_22_linux_kernel_module-master$ 

```

Checking the error online produced the information that secure boot might interfere with this process I disabled secure boot in the BIOS, but the result remains the same.

I'm at the point of rolling back my installation to 20.04 as 22.04 has proved to be such a dud for me, with several other necessary packages not working, not least samba shares being broken, and on an LTS as well.

---

