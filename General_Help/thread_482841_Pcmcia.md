---
title: "Pcmcia"
date: 2007-06-24
forum: General Help
---

### Post by hellstern on 2007-06-24
Hi,
I want to install a version of AstLinux(Asterix) on a 1 gb Compact Flash card. I have a PCMCIA Compact Flash card reader. The version of Ubuntu is 7.04 and the laptop is a IBM X41.

I have done: *sudo fdisk -l* and gets this result:

[I]    Device Boot      Start         End      Blocks   Id  System
    /dev/mmcblk0p1               1         984     1983619+   6  FAT16[/I]


Then I wants to run this command: 
[I]
   sudo gunzip -c AstLinux-0.4.5-net4801.img.gz > /dev/mmcblk0pl[/I]

Then I get: bash: */dev/mmcblk0p1: Permission denied*

I don't know if bash: /dev/mmcblk0p1 is the right device or how to get around the permission problem. I can do this on a Windows PC but I wants to learn how to do it in Linux – Ubuntu so any help is received with thanks :-)

/Tue

---

### Post by fjonasch on 2007-08-25
Hi!

I think your problem is the following: You can't write to /dev/mmcblk0p1 because this is a so called "block device". It's needed to mount your flash card in your filesystem e.g. under /home/yourname/cfcard. Does the card appear under places or computer (this would mean it's automaticly mounted...)? If not, you need to mount it by hand in your filesystem, which works like this:

```

mkdir cfcard
sudo mount -t vfat /dev/mmcblk0p1 cfcard

```

The first line creates a folder called "cfcard", the second line tells the system to show the content of your CFcard "/dev/mmcblk0p1" in the folder "cfcard". Now you should be able to unzip the AstLinux-file into this folder...

fjonasch

---

