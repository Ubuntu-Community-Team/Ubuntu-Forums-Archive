---
title: "Installation error with graphics monitor usb driver"
date: 2021-04-17
forum: General Help
---

### Post by MZ250Supa5 on 2021-04-17
For the past few years I've been using a Parblo Coast 22 graphics monitor, sometimes with a few issues along the way, but up until now relatively easily resolved. However after having not used the graphics monitor since upgrading to Ubuntu MATE 20.04 I've recently brought this monitor back into use. I don't want to have to return to Windows in order to use this piece of kit, so would appreciate any help available in getting this thing working again!

I've followed the installation directions, but the result is as below:

```
xxxx@efnisien:~$ cd Monoprice_22_linux_kernel_module-master/
xxxxi@efnisien:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/5.8.0-50-generic/build M=/home/xxxx/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-5.8.0-50-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.8.0-50-generic'
xxxx@efnisien:~/Monoprice_22_linux_kernel_module-master$ sudo make install
[sudo] password for xxxx: 
cp ./mono_22.ko /lib/modules/5.8.0-50-generic/kernel/drivers/input/tablet/
echo mono_22 >> /etc/modules
depmod
cp ./load_mono_22.sh /usr/local/bin
cp ./detach_usbhid /usr/local/bin
cp ./load_mono_22.rules /etc/udev/rules.d
/sbin/udevadm control --reload
make: /sbin/udevadm: Command not found
make: *** [Makefile:27: install] Error 127
xxxx@efnisien:~/Monoprice_22_linux_kernel_module-master$
```

I've done a few checks and I know that gcc is on the system (version 9.3.0) and that udevadm is also there, so I don't understand why I'm getting the error. I've looked online for explanations, but those I've found are way above my head, but this might be down to differences in communication/comprehension.

---

### Post by CelticWarrior on 2021-04-17
Let's start with the obvious:

```
sudo apt install build-essential
```

---

### Post by Holger_Gehrke on 2021-04-17
'udevadm' used to live in /sbin but nowadays resides in /bin. Up to Ubuntu 18.04 there was a symbolic link in /sbin, but according to packages.ubuntu.com that link isn't installed anymore. So there's two easy fixes to this problem: either create a link in sbin or remove the s from 'sbin' in the Makefile.

Holger

---

### Post by MZ250Supa5 on 2021-04-17
I should have added to my original post that I had tried the 'obvious' but thanks for the suggestion. Sometimes we wrongly eschew the obvious :)

---

### Post by MZ250Supa5 on 2021-04-17
Thanks Holger, editing the Makefile solved the issue.

---

