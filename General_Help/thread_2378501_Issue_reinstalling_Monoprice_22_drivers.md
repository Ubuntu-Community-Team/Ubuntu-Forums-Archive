---
title: "Issue reinstalling Monoprice 22 drivers"
date: 2017-11-23
forum: General Help
---

### Post by MZ250Supa5 on 2017-11-23
I've been using this driver for my Parblo Coast 22 since I got it in February. [https://github.com/odysseywestra/Monoprice_22_linux_kernel_module](https://github.com/odysseywestra/Monoprice_22_linux_kernel_module) Normally it installs well and works with no problems, though it is rather reluctant to be persistent in Ubuntu for any great length of time, despite it being installed correctly as per the directions. As I have a 3 monitor set-up, (including the pen monitor itself) I need to use a utility to define the screen area to be used by the pen monitor, which needs to be reconfigured after every startup/logoout. This is trivial, and takes seconds, however, at times the driver to be loaded is missing, so it needs to be reinstalled, a matter of a minute in a terminal does the trick. However, and I'm suspecting that a system upgrade earlier today has broken something, as I just rebooted and found that the driver was once again missing, so I attempted to reinstall. I got an error messsage thus:

```
padi@padi-penbwrdd:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/4.10.0-40-generic/build M=/home/padi/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-40-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-40-generic'
padi@padi-penbwrdd:~/Monoprice_22_linux_kernel_module-master$ sudo make install
[sudo] password for padi: 
cp ./mono_22.ko /lib/modules/4.10.0-40-generic/kernel/drivers/input/tablet/
echo mono_22 >> /etc/modules
depmod
cp ./load_mono_22.sh /usr/local/bin
cp ./detach_usbhid /usr/local/bin
cp ./load_mono_22.rules /etc/udev/rules.d
/sbin/udevadm control --reload
modprobe mono_22
modprobe: ERROR: could not insert 'mono_22': Exec format error
Makefile:21: recipe for target 'install' failed
make: *** [install] Error 1
padi@padi-penbwrdd:~/Monoprice_22_linux_kernel_module-master$ https://github.com/odysseywestra/Monoprice_22_linux_kernel_module

```

I've done a bit of searching, and the only solutions I have found have referred to using a 'sudo make install' command to fix the problem, but that won't suffice in my situation, as I'm already doing just that. It's pretty crucial that I get the pen monitor working soon, as it's something I use every day, and though I don't need it to earn a crust, it's very frustrating not having access to a tool I use a lot.  I've done a dmesg | tail and this is the output:

```
padi@padi-penbwrdd:~$ dmesg | tail
[   39.192045] nvidia-modeset: Allocated GPU:0 (GPU-ea92c10b-7e0b-ae89-a4d7-bd53663c5a3b) @ PCI:0000:01:00.0
[   51.480824] Non-volatile memory driver v1.3
[   80.928225] ISO 9660 Extensions: Microsoft Joliet Level 3
[   80.961689] ISO 9660 Extensions: RRIP_1991A
[   83.044637] Bluetooth: RFCOMM TTY layer initialized
[   83.044642] Bluetooth: RFCOMM socket layer initialized
[   83.044646] Bluetooth: RFCOMM ver 1.11
[  230.386661] mono_22: version magic '4.10.0-28-generic SMP mod_unload ' should be '4.10.0-40-generic SMP mod_unload '
[  371.196996] mono_22: version magic '4.10.0-28-generic SMP mod_unload ' should be '4.10.0-40-generic SMP mod_unload '
[  408.795503] mono_22: version magic '4.10.0-28-generic SMP mod_unload ' should be '4.10.0-40-generic SMP mod_unload '
padi@padi-penbwrdd:~$ ^C
padi@padi-penbwrdd:~$ 

```

So it looks like it is something that's happened after having upgraded my system, which was working great prior to rebooting and using the new kernel. Now all I need to know is how to change things so the driver works as it should. Any help would be much appreciated.

---

