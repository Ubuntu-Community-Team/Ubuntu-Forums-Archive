---
title: "Grub help"
date: 2007-09-16
forum: General Help
---

### Post by triptoe on 2007-09-16
Edit: Solved... for some reason when i tried this and did one of the first howtos i saw... instead of typing sudo grub.. i typed grub.. and when i did find /boot/grub/stage1 it did not return anything

i've followed some guides but nothing is working... windows overwrote my grub install.

i am attaching a screenshot of what my current gparted looks like.

i still can't seem to reinstall grub

i just want to install grub.. and the "firing up the live install , and doing mounting the partitions with gparted thing" didn't work... it never reinstalls grub. i even tried to just reinstall ubuntu all over but it hung at 90 minutes... and i am tired of wasting hours of my time

> Step 1: Log in a root console.
Step 2: Execute "grub".
Step 3: In the grub shell just type:

root (hd0, 3)
setup (hd0)

this didn't work. first of all i am using a serial drive not a hard drive. so i tried to get the installation on my second serial drive on the third partition working

> grub> root (sdb0,3)

Error 23: Error while parsing number

grub> root (sd1,3)

Error 23: Error while parsing number

grub> root (sd0,3)

Error 23: Error while parsing number


> grub> root (hd1,3)

Error 21: Selected disk does not exist


I also tried this which doesn't work:

> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.


sudo grub
find /boot/grub/stage1

(hd1,2)

---

