---
title: "[SOLVED] Howto compile and install kernel 2.6.23.1"
date: 2007-12-11
forum: General Help
---

### Post by quandary on 2007-12-11
Absolute beginner talk is probably the wrong forum for your question. Check out the programming forum.

For your question:
Hm, you get any errors and warnings from the compiler?


Did you compile the new kernel and forgot to enable PCI support???

Here is how to get to a new kernel correctly:


cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2)
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2.sign](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2.sign)


apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2


tar xjf linux-2.6.23.1.tar.bz2
ln -s linux-2.6.23.1 linux
cd /usr/src/linux

***
Apply patches here
***

cp /boot/config-`uname -r` ./.config
make menuconfig

*** Build the kernel
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
*** Finished building the kernel

cd /usr/src
ls -l
*** On my test system they were called linux-image-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb 
*** (which contains the actual kernel) and 
*** linux-headers-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb 
*** (which contains files needed if you want to compile additional kernel modules later on). 

*** Install them
dpkg -i linux-image-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb

*** (You can now even transfer the two .deb files to other Ubuntu systems 
*** and install them there exactly the same way, 
*** which means you don't have to compile the kernel there again.)

vi /boot/grub/menu.lst



*** Now reboot the system:
shutdown -r now

*** If everything goes well, it should come up with the new kernel. 
*** You can check if it's really using your new kernel by running
uname -r

***This should display something like
--------------------
|                  |
| 2.6.23.1-custom  |
|                  |
--------------------

If the system doesn't start, restart it, and when you see this:
--------------------------------------------------
|                                                |
| GRUB Loading stage 1.5                         |
|                                                |
|                                                |           
| GRUB loading, please wait...                   |
| Press 'ESC' to enter the menu... 1    _        |
|                                                |
--------------------------------------------------

press ESC to enter the GRUB menu:
Select your old kernel and start the system. 
You can now try again to compile a working kernel. 
Don't forget to remove the two stanzas of the not-working kernel from /boot/grub/menu.lst.


Afterwards it might be that your sound and your wireless network won't work anymore. If so, you will have to download, compile and install the latest alsa driver, as well as the latest wireless drivers and firmware. You can always boot the older version of the kernel, where sound and network will work for sure.

---

### Post by K.Mandla on 2007-12-20
Moved to General Help.

---

### Post by quandary on 2007-12-25
How to install the latest sound driver, you can read in my post here:
[http://ubuntuforums.org/showthread.php?p=4011326](http://ubuntuforums.org/showthread.php?p=4011326)

The wirless drivers, i use Intel Pro Wireless 2200 BG
I had to download, compile and install the latest drivers, and it worked well again.

You can find the latest drivers & firmware for Intel Pro Wireless 2200 BG at:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

If you don't know your wireless card, type the following on the command line:
```

 lspci | grep "Network controller"

```

which should show something like
```

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

If you have a normal network card, type:
```

lspci | grep "Ethernet controller"

```

And you shold get something like:
```

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

---

