---
title: "Lost Grub Loader Cannot open UBUNTU"
date: 2015-01-08
forum: General Help
---

### Post by Dyffo on 2015-01-08
I have Windows Vista/ Ubuntu on dual boot on my computer "C" drive - this was working perfectly until I installed Windows 7 on to my computer drive "E".
On start up I am offered either Windows 7 or Vista but no Ubuntu.
Ubuntu is still installed on to Drive "C" but I can't access it.
How do I restore Grub Loader  so that on Start up I am offered Ubuntu - Windows 7 and Windows Vista.

---

### Post by yancek on 2015-01-08
If you had Ubuntu installed on what you refer to as your 'C' drive (partition actually) then you used a wubi install.  This simply installs Ubuntu as a program inside windows.  It is no longer supported.  If you installed windows 7 on what you refer to as your 'E' drive, this might be a logical partition.  If it is a logical partition, then windows 7 would have installed its boot files to the C partition thus overwriting your vista boot files so there went your Ubuntu entry.

I've never done a wubi install but my understanding of it is that it creates an entry in the windows boot file pointing to the Grub bootloader of Ubuntu.  It's not Grub, it's your windows boot file that needs repair.  You might try downloading, installing and using EasyBCD on windows 7 to create an entry for Ubuntu although I don't know if that works with wubi.  You might wait for someone more familiar with wubi to post a suggestion.

---

### Post by kpatz on 2015-01-08
I think the OP is referring to C and E as physical drives, not partitions.

Installing Windows 7 overwrote grub with the Windows boot loader.

The easiest way to fix this is to boot from the Ubuntu live CD/DVD or USB drive and then install the Boot-Repair tool.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> 
either from an Ubuntu live-session (boot your computer on a Ubuntu live-CD or live-USB then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it)

- connect to the Internet

- open a new Terminal, then type the following commands (press Enter after each line):

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair


```


---

### Post by Dyffo on 2015-01-08
Hi and thanks - kpatz - you got it and all is repaired. Thanks once again

---

