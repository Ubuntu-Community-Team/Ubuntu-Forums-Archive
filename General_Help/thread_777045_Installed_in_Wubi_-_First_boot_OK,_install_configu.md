---
title: "Installed in Wubi - First boot OK, install configures then no boot."
date: 2008-05-01
forum: General Help
---

### Post by DaveBG on 2008-05-01
Hi.

I just installed ubuntu 8.04 in my Windows XP os on partition F:\.

Installs OK. Says i have to reboot.
I reboot and i get the boot manager with the Ubuntu option.
I choose Ubuntu and it loads fine. I see the orange art background.
It starts to "checking your installation" and does this for about 3-4 minutes automatically on the first boot.
Then it reboots and it cant find boot partition.
I get Grub manager and none of its options work. Ubuntu or UbuntuSafeMode. It only can load XP...

I reinstalled and used a manually downloaded ISO so that it wont need to DL and get the same.

Here is how it looks in windows: (red circle show where it is installed with 10GB space and all other standard options in Wubi)
[[img]http://img528.imageshack.us/img528/8936/26687731ok0.th.jpg[/img]]("http://img528.imageshack.us/my.php?image=26687731ok0.jpg")


Here is my boot ini:

> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /sos
c:\wubildr.mbr="Ubuntu"


Here is Grub menu:

> ## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=D4A914212AD68FC3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=D4A914212AD68FC3 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)/ubuntu/disks
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Please help!
Ubuntu 7 used to work this way.... this does not. :confused:

---

### Post by ago on 2008-05-01
In the grub menu replace all

root (hd0,4)/ubuntu/disks 

with 

root ()/ubuntu/disks 

and also replace groot=(hd0,4)/ubuntu/disks with groot=()/ubuntu/disks

---

### Post by DaveBG on 2008-05-01
Thank you! It works. It booted perfectly.

---
Now my MX1000 Lazer mouse was working only the first 5 minutes then stopped out of a sudden and i cannot connect to my wirelesses router (have no net) then when i tried to switch users it just freezed then reset PC after 15 secs and asks me for the password every few clicks but i will iron those in time :)

Seems great OS!

---

