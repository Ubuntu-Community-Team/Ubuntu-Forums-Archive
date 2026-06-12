---
title: "File could not be parsed or opened"
date: 2018-07-27
forum: General Help
---

### Post by Gnusboy on 2018-07-27
I'm getting this error when I try to update Ubuntu 16.04

E:Could not read from /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_InRelease - getline (21: Is a directory), E:The package lists or status file could not be parsed or opened.
It's also supposed to be a serious problem. I have looked through the various files and have found a couple of ways that might fix my problem, but they are all several years old. What is the current repair?
This problem crept up as I was trying to clean my system from a different problem. I ran fsck and everything came up good, but then this problem showed up. Are they related?

And I need to backup my system before attempting the fix, but I keep getting 
"Error creating directory: No space left on device"
I get this while trying to backup to a nearly empty 462 GB external drive. It always seem to happen when I use Deja Dup, but I haven't found an easy to use program to replace it.
Help for either problem will be appreciated. Thank you.
Jess

---

### Post by 0xd3bugd on 2018-07-28
Parse I am not sure about, but I have had issues that certain files didn't have read and write access when they should have, restart helped.
maybe someone else can help with the parsing. 

> [COLOR=#000000]And I need to backup my system before attempting the fix, but I keep getting [/COLOR]
[COLOR=#000000]"Error creating directory: No space left on device"[/COLOR]
[COLOR=#000000]I get this while trying to backup to a nearly empty 462 GB external drive. It always seem to happen when I use Deja Dup, but I haven't found an easy to use program to replace it.[/COLOR]

Did you format your new hard drive? Do you have read and write privileges on it? Try running commands as root.

[COLOR=#333333][FONT=&amp]fdisk -l

says what when you have usb inside? 

if you want **format the drive, and start over since its just a BACK UP.** with

umount /dev/sdb1 (usually your usb - on debian like systems like mint and ubuntu)

mkfs.vfat -n "DEVICENAME" -I /dev/sdb1

[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-07-28
Try terminal command ```
sudo rm /var/lib/apt/lists/* 
``` and then immediately run ```
sudo apt update
``` to recreate the lists which have become corrupt for some reason.

It is most unlikely that the problem has anything to do with running fsck, but depending on how deja-dup works, (and I've never used it so don't know details), and what filesystem you have on the external disk, you may have inadvertently made unknown and problem changes to the permissions of those list files.  It is always best in my experience to back up your files and folders to a partition/disk formatted with a Linux filesystem, eg ext3 or ext4, which will retain permissions if you use the correct backup application.

---

### Post by Gnusboy on 2018-07-28
> **ajgreeny said:**
> Try terminal command ```
sudo rm /var/lib/apt/lists/* 
``` and then immediately run ```
sudo apt update
``` to recreate the lists which have become corrupt for some reason.

It is most unlikely that the problem has anything to do with running fsck, but depending on how deja-dup works, (and I've never used it so don't know details), and what filesystem you have on the external disk, you may have inadvertently made unknown and problem changes to the permissions of those list files.  It is always best in my experience to back up your files and folders to a partition/disk formatted with a Linux filesystem, eg ext3 or ext4, which will retain permissions if you use the correct backup application. 

Hey, Hi and thanks for answering.
I didn't think it was an fsck error. Initially, there were a number of problem files. After I ran an fsck, all appeared to be OK. The only one not fixed was the one I asked about. It shows as a serious problem (it won't fetch updates so it could make my system vulnerable - at least that's my take away.)

From what I've read there's a chance I could goof stuff up. I can mostly handle the terminal, but only if I have the commands outlined. I'll try your set and hopefully it will work. 

Backing up my system has always been a problem using deja dup. The only time it worked as it should was when I installed the 1TB external drive, which I formatted to Linux EXT4 on install. But Deja Dup has not worked since.  For some reason, I can't get it to backup anything and I does not alllow me to do a copy/pastuse the automatic scheduled backup and it won't work with the back up now feature.
If I try to jigger it, I get the "you don't have permission to change files." That's nuts. I have all my working directories set on read and write. I'm not sure, but I think I may have set a password back in 2009 when I started using Ubuntu. And that password turned to dust a long time ago.  I recently found a set of commands for changing that password, but I be very worried about losing my stuff. It's like Catch 22.
I should just learn a new backup utility, but I find most sets of directions for programs are anti-intuitive and they devour my time and confidence.
Anyway, I'll try your suggestion. I'll let you know how it goes.
Thanks.

---

