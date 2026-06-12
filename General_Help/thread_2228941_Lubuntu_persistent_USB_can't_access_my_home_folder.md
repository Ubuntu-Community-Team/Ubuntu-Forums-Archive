---
title: "Lubuntu persistent USB can't access my /home folder in hard drive"
date: 2014-06-10
forum: General Help
---

### Post by zakafreakarama on 2014-06-10
Hi everyone.

Okay, this is something that seems to happen with all *buntu variants and it's annoying me. I've created a persistent USB installation of Lubuntu 14.04 in a 8GB pen drive, complete with its casper-rw and home-rw partitions. It works like a charm in at least 4 different machines, but I'm having some problems with my own Linux laptop. When booting from my Lubuntu pen drive, I have no problems to access the hard drive in machines with Windows installed. I can mount all the hard drives and partitions and browse through the filesystems easily. However, whenever I use my portable OS to access a Linux box, I seem to lack privileges to access the folders and files in the hard drive's /home partition. There are personal files in my /home that I'd like to copy to my portable filesystem (including customization themes that I can't find online anymore), and I just can't. Whenever I try, I get a 'permission denied' message. My laptop runs Linux Mint Debian Edition  032014, with sources modified to track Debian Testing (Jessie). 

I have to point out that this didn't happen when I tried other Live distros in my pen drive. I've tried both Debian Live and Knoppix, and both let me browse through my own filesystem without any trouble. But Lubuntu and Xubuntu just won't let me do it. And it's a pity; I intended my Lubuntu pen drive to replace my Knoppix drive as my portable OS. But with such a limitation, I just can't.

Any suggestions will be much appreciated. By the way, my original plan was to create a Debian Stable (Wheezy) pen drive, but I just couldn't get persistence with it, no matter how I tried. Lubuntu looks like a great alternative, but this is sabotaging my plan.

Thanks a lot.

---

### Post by sudodus on 2014-06-12
Welcome to the Ubuntu Forums :-)

I think you have problems with permissions (read/write/execute for directories and files).

If you unmount the partition with problems (let us say it is **/dev/sda1**) and remount it and use superuser privileges, you should be able to do what you want.

```
sudo umount /dev/sda1
sudo mkdir /mnt/sda1

sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1/home

```
and you can list files, copy files etc (with superuser privileges if necessary)

```
sudo cp -p /mnt/sda1/home/some-directory/some-file /path-to-target
```
-o-

Be careful when using sudo, avoid overwriting or deleting important files.

---

