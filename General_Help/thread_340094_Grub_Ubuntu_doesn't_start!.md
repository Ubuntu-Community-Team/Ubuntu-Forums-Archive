---
title: "Grub: Ubuntu doesn't start!"
date: 2007-01-16
forum: General Help
---

### Post by Cocio_16 on 2007-01-16
Hello!
Sorry for my English, I tried on the french forum, but they don't look able to help me :p
Hope that you will understand all.

Monday, I tried to install Gentoo on an other partition... it was long, I wanted to sleep, so... I stopped it.
I had say to Gentoo to install his own Grub. 
Gentoo doesn't had the time to completed his installation because I stopped it...
When I rebooted my computer, grub doesn't work.
Error 17 : ( cannot mount sellected partition) 
(if you want to know)
So, I re-installed Grub with the Ubuntu live CD.
When I choose Ubuntu (it's the same for the recovery), I have
> BusyBox v1.1.3 (Debian 1:1.1.3-ubuntu3)Built-in shell (ash Enter 'help' for a list of built commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [17179580.180000 ohci1394:fw-host0: SelfID received. outside of bus reset sequence
Windows XP boot  correcly.

Since, I installed Debian (and it work well)
I asked to Debian to install his own Grub: it's always the same error for Ubuntu.


What I can to do?
Do you need more information?

---

### Post by Rippey on 2007-01-16
looks like your initramfs is broken, if that's true here's a way to fix it:
boot from live cd.
open terminal.
mount your ubuntu disk (asuming it's hda1: sudo mount -t "filesystem" /dev/hda1 /mnt)
then "sudo mount -t proc /proc /mnt/proc"
after that type "sudo chroot /mnt"
now you are ready to repair your initramfs
go to /boot and check what kernel version ubuntu is using(should be lots of files there with the kernel version in there name(2.6.15-27-k7 is the 1 I'm using))
**_don't use uname -r becouse that will show you the kernel of the live cd_**
type "sudo update-initramfs -u -k *kernelversion*"
wait for the command to finish
type "exit"
and reboot

---

### Post by Cocio_16 on 2007-01-16
I tried :)
it doesn't worked...

For exemple, I have
abi-2.6.17-10-generic
I wrote 
sudo update-initramfs -u -k 2.6.17-10-generic
it's the good thing or I am stupid? ( :( )

I did it with the live CD, but... it's really long to boot!
It's okay if I use Debian next time? (I know that certain commands will not be exacly the same)

---

### Post by zzzname on 2007-01-17
I had the same problem and I followed the advice in the last post of [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59792](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59792)
+ I reinstalled ubuntu-minimal as well. Now it's working just fine.

---

