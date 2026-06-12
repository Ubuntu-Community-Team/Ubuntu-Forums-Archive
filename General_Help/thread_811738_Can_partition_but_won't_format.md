---
title: "Can partition but won't format"
date: 2008-05-29
forum: General Help
---

### Post by HuntMike79 on 2008-05-29
Ok, I'm trying to install kunbuntu but for some reason it cannot format my hard drive.

Gparted takes ages to load, and I can make a partition ok, but when I try and format it (ext2), the program says it cannot.

How can I fix this?

FWIW, XP can partition and format my drive with no issue. My drive is 250gb Pata

EDIT: I seem to have it working now, I tried "install mode" on booting...

---

### Post by jimbob on 2008-05-29
How are you loading Gparted?  Why do you want to use ext2?  Ext3 is better - ext2 with journaling.

---

### Post by HuntMike79 on 2008-05-29
Well, I thought I had it working for a minute. I'll go for ext3, I wasn't really sure which one to go for anyway. :o

Right, I've totally wiped the drive with Gparted (i do sudo gparted in terminal to load it).

I loaded xubuntu in install mode, went "Guided - use entire disk", but it fails, this is what it says:

"Failed to create a swap apace 

The creation of swap space in partition #5 of SCSI2 (0,0,0) (sda) failed."

So something isn't working right... :(

EDIT: Tried gparted again from the terminal, this error might make more sense?

"Input/ouput error during read on /dev/sda"

WTH is going on?

---

### Post by housam on 2008-05-29
download and burn the [[COLOR="Red"]_Gparted iso_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") to make a live cd then boot from it . 
wipe your HDD and create 3 new partitions .
- one for the root (/) ext3 format - 10-20 GB
- one for the swap - 2 GB is ok
- the rest for /home ext3 format
boot from Ubuntu live cd and start installing the system. when it comes to the partitioning choose the manual way and assign the root partition ( / ) only and don't format any thing .and continue.
good luck

---

### Post by HuntMike79 on 2008-05-29
> **housam said:**
> download and burn the [[COLOR="Red"]_Gparted iso_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") to make a live cd then boot from it . 
wipe your HDD and create 3 new partitions .
- one for the root (/) ext3 format - 10-20 GB
- one for the swap - 2 GB is ok
- the rest for /home ext3 format
boot from Ubuntu live cd and start installing the system. when it comes to the partitioning choose the manual way and assign the root partition ( / ) only and don't format any thing .and continue.
good luck
I've just downloaded the gparted CD and it worked perfectly. Thanks! I just need to boot the kubuntu CD and install. :)

EDIT:Kunbuntu didn't see any of the partitions, even tho I know that they are there.  I tried a windows XP live CD and I could see all 3 partitions yet kubuntu doesn't find any. Help! :(

---

### Post by HuntMike79 on 2008-05-29
I've fixed it, I've taken all the PCI cards out my system and it now finds the partitions ok. 

I think it must've been some hardware conflict.

I've put my wifi card back in, again no issue, but as soon as I put the Audigy 2 soundcard in, it screws everything up.

I'll try it in a different slot, or a different soundcard altogether as creative cards are poo anyway. :)

---

### Post by housam on 2008-05-30
> **HuntMike79 said:**
> 
Kunbuntu didn't see any of the partitions, even tho I know that they are there.  I tried a windows XP live CD and I could see all 3 partitions yet kubuntu doesn't find any. Help! :(

Did you managed to format the partitions to ext3 for (/) and /home , and swap for the swap ? because ubuntu partitions can not be detected through windows unless you install some special software.!!

---

### Post by HuntMike79 on 2008-05-30
> **housam said:**
> Did you managed to format the partitions to ext3 for (/) and /home , and swap for the swap ? because ubuntu partitions can not be detected through windows unless you install some special software.!!

No I partitioned and formatted the drive using gparted, then booted the ubuntu live cd.

When installing the live CD couldn't find any of the partitions with the sound card in. 

So I removed the soundcard and everything works now. :)

---

### Post by housam on 2008-05-30
So, you installed Ubuntu and  it works fine . Glad to hear that. have fun
cheers

---

