---
title: "Target filesystem doesn't have requested /sbin/init"
date: 2017-04-20
forum: General Help
---

### Post by tehmunkee on 2017-04-20
I'm having an issue. I've scoured the internet and found a few peoples solutions but they do not work for me because of what I think is a related issue.

First, if I try to go to boot up, I end up getting this screen

[ATTACH=CONFIG]274680[/ATTACH]

I am currently booting from a usb drive ubuntu, and from there I have found [this](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html) referenced in every single solution, or some form of fsck that doesn't work

But, I think that is because of this error that happens if I try to mount it at all:

ubuntu@ubuntu:~$ sudo mkdir /mnt/hd
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/hd
mount: /dev/sdc1: more filesystems detected. This should not happen,
       use -t <type> to explicitly specify the filesystem type or
       use wipefs(8) to clean up the device.

I can mount if I do mount -t ext4, and I can access all my files on the drive, but wipefs does not do anything at all and still will show that error when trying to mount. I believe this to be the cause of why I can't boot, but I can't seem to fix it (of course, I could be wrong on the reason too). I've also scoured the internet to find a fix for that on why an operating system can't boot but everything I find seems to be for just a second hard drive and not the primary.

Any help is much appreciated.
Thanks

---

### Post by Bashing-om on 2017-04-21
tehmunkee; Hello; Welcome to the forum .

The basis of all trouble shooting a hard drive begins with what bios sees .
Does bios recognize all the hard drives ? If bios does not see it, can not pass to the operating system what it does not know. 

Next IF bios sees the drive is what is the partitioning like ?
Consistent ?
From the liveUSB post back - Between code tags, please - the output of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
where here 'fdisk' may or may not be the correct tool to look - fdisk is for the legacy (MBR) partitioning.

IF both the aboves are consistent, we next then attempt to mount the install root partition and see what files are inplace and/or corrupted .

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

