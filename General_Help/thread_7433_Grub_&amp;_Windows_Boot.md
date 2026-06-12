---
title: "Grub &amp; Windows Boot"
date: 2004-12-07
forum: General Help
---

### Post by Eraph on 2004-12-07
Okay, here's the deal - I'm running a dual boot on my computer, both OS's on seperate partitions of the same physical drive. On one partition, Windows XP, and on another, Ubuntu. When I installed Ubuntu, I also installed the GRUB loader, but now I want to get rid of it in favour of using Windows XP's loader.
So step 1: Remove GRUB. I figure the best way to do this is to use the WinXP install CD to do the FixMBR thing that it does.
Step 2: Set up the boot.ini file in Windows XP. Trouble with this is... I don't exactly know what I should add :/
Currently, it looks like this:
[b][INDENT][boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn[/INDENT] [/b]
So I need to know what sort of text to add to that, and what the number of the partition is for the Ubuntu drive, right? I'm using Partition Magic 8.0, and it doesn't seem to display this - I guess counting the partitions in the drive isn't the best of ideas, so this is where I call for some help!

Thanks.

---

### Post by Magneto on 2004-12-07
go here [http://www.linuxforums.org/forum/topic-3573.html](http://www.linuxforums.org/forum/topic-3573.html)

look halfway down the page for your answer

---

### Post by Eraph on 2004-12-07
Well, unsurprisingly, it didn't work. I did the whole floppy disk thing, and when I choose Ubuntu from Windows OS select, all I get is a black screen with a flickering cursor.
When I set up Ubuntu, I installed it all onto the one partition, so would that be causing problems when trying to get the 512 byte of the boot sector?
Also, the MBR fix for WinXP didn't get rid of GRUB, but I want to ignore that for now (its just as well it didn't - I wouldn't have been able to get back into Ubuntu), and just get this Windows OS select thing working.

---

### Post by Magneto on 2004-12-07
is the windows partition still showing the boot flag?

---

### Post by Eraph on 2004-12-07
[QUOTE=Magneto]is the windows partition still showing the boot flag?[/QUOTE]
 Er... How do I know?

---

### Post by Darkenbay on 2004-12-07
I just went thur same thing.
I think I may have got lucky but all i did was reinstalled windows then reinstalled ubuntu and grub when it detected other pation.
this seemed to resolve the issue.

2nd i feel i should state that i didnt modify the partions just formated the partions and reinstalled the os's.

---

### Post by Magneto on 2004-12-07
[QUOTE=Eraph]Er... How do I know?[/QUOTE]
 the easiest way is 
```
sudo cfdisk /dev/hda 
```

you have a few problems here and I am willing to help but you really shouldnt be attempting something as serious to your computer as this without knowing what you are doing. You obviously know what you want to do but you have read up on the how

Your windows partition has a boot flag set for it during the windows installation process - if this is gone it wont boot
IF you dont have the right partition information in your bootloader the system wont boot

please read up on partitions and boot loaders

id suggest reading the booklet that came with Partition Magic 8.0 which explains all these concepts they apply to all PC hardware regardless of Operating System

also read the documentation for GRUB 

once youve read that follow the instructions on the link I posted and you will have your system the way you want it.   [www.google.com](www.google.com)

every question you can think to ask on this topic has an answer on google.com

try looking up " what is a boot flag? " on google
the answers come quicker than any message board

---

