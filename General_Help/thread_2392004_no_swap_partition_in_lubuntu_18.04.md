---
title: "no swap partition in lubuntu 18.04?"
date: 2018-05-15
forum: General Help
---

### Post by gryphus-one on 2018-05-15
Hello, I'm new to the forum. Excuse me if my English is not perfect, since it's not my first language.

I started using Linux at the end of 2008 or beginning of 2009 with Ubuntu. Shortly after I also tried other distros like Mandriva and Linux Mint. Then, at the end of 2011 or beginning of 2012, for some reasons I stopped using Linux, and now I'm returning to it.

I have a very old laptop, an Acer Aspire 5670 that I bought in 2007, so I have to use a 32 bits distro and a lightweight desktop environment, hence I have chosen Lubuntu 18.04 desktop 32 bits. After checking the .iso with MD5, SHA1 and SHA256 I created a bootable USB stick with Etcher.
My laptop had 1GB of RAM when I bought it (it had 2 modules of 512MB each), but currently it has one 2GB module. Apart from that, I have just swapped its hard disk for an entirely blank one, because I wanted Lubuntu installation to take it all as my only operating system (I don't plan on using Windows in this old computer anymore), while still preserving my old Windows installation and data in their own disk.

The question I have is the following: when I installed Linux distros in those old times, I remember that by default the installation program used to create a swap partition, without me having to create it manually with the GParted included in the installation program for more advanced and custom installation settings. Now, when I installed Lubuntu 18.04 I just selected the option to wipe the entire hard disk (which was already selected by default after the installation program detected that no operating system was installed in the hard disk) and let it do the rest automatically, without using GParted or any of the advanced options, hoping that the installation program would make the best choice according to my hardware. However, after completing the installation I have analyzed my hard disk with GParted just to find that the Ext4 partition is taking the whole hard disk and that there's no swap partition!! Should I create one myself with the GParted of my USB stick? any risk of corrupting or losing data from my Ext4 partition when shrinking it to make room for swap? Or is there a possibility of creating a swap file inside the Ext4 file system, just like Windows has pagefile.sys in the main file system without a partition exclusively for that?

Thanks in advance.

EDIT: I have found out that Linux is now using a swap file in the main file system, instead of a separate and exclusive swap partition.

---

### Post by deadflowr on 2018-05-15
> Or is there a possibility of creating a swap file inside the Ext4 file system, 
That
from Ubuntu 17(.04?) on all fresh installs will use a swapfile.
If you have a swap partition already it'll be used.
But by default, if no swap partiton is found on any of the connected disks, it'll make a swapfile.
The lone exceptions are lvm installs. From what I know.

Explained all here:
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu]("http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu")

---

### Post by oldfred on 2018-05-15
You already should have a swap file.
cat /etc/fstab

See release notes. Installer will create swap file, but will use an existing swap partition if found.
       [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

---

### Post by gryphus-one on 2018-05-15
Hey, thank you two, I have checked and yes I do have a swap file in the root of my file system, thank God!!
I didn't know Linux had switched from swap partitions to swap files, as I said before I have been out of the Linux world for some years and in the past it used to swap in a separate partition. And personally I think it's better now, because a swap file can be enlarged, shrinked or even deleted (if someone wants to) much more easily than an exclusive partition for it. As I said, Windows (and probably Mac OS too) has always used a page file and I think it's the logical way to go, so congratulations to whoever decided to make this change ;)

---

### Post by deadflowr on 2018-05-15
> I didn't know Linux had switched from swap partitions to swap files, 
Distributions all do things differently.
So while Ubuntu now goes one way, it does not mean another will go the same way.

---

### Post by gryphus-one on 2018-05-15
> **deadflowr said:**
> Distributions all do things differently.
So while Ubuntu now goes one way, it does not mean another will go the same way.

Ohh, so it's not a kernel thing? In any case, when it comes to domestic users Ubuntu is the MAIN Linux distro.

---

