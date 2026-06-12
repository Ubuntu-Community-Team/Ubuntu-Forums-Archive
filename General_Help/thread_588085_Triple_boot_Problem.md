---
title: "Triple boot Problem"
date: 2007-10-23
forum: General Help
---

### Post by sagarin on 2007-10-23
I have installed XP and Ubuntu. No problems until i installed Fedora 7 for a triple boot.
Now i am not able to boot ubuntu. The error was 

rootnoverify(hdo,7)
chainloader +1
Error 13:Invalid or unsopported executable format

I installed Fedora as the third OS. Can you specify how to get back to Ubuntu, with Fedora and XP?

---

### Post by dayvy on 2007-10-23
The error your getting looks like it's related to your xp portion of your menu.lst. However, read below to fix your ubuntu boot.


Which os contains the grub menu.lst, Ubuntu or Fedora? If it's Ubuntu then you can boot into Fedora and mount the Ubuntu partition that has the /boot directory and then repair the config file. Make a directory in /mnt called ubuntu then mount it there:

cd /mnt
mkdir ubuntu
mount /dev/put_appropriate_partition_here /mnt/ubuntu
cd /mnt/ubuntu
cd to the /boot/grub directory and edit the menu.lst file. It should look something like this:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e81b4944-1eab-4290-9a7e-b6d811cc6b38 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

Your XP entry should look something like this:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

