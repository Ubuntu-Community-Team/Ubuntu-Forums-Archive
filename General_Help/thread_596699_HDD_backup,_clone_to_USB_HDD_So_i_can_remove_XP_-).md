---
title: "HDD backup, clone to USB HDD So i can remove XP :-)"
date: 2007-10-29
forum: General Help
---

### Post by scotthammy on 2007-10-29
[COLOR="DarkGreen"]Hi Everonye,

**First off, Im Really happy with Gutsy 7.10. 99.99% ex MS user**.[/COLOR]


[COLOR="Green"]**Now Q.**[/COLOR]
[COLOR="DarkRed"]Im looking for a way to make a Full hard drive copy onto a USB HDD, with compresion and some form of GUI. text based would rock. 

I have had a look at clonezilla and g4l(ghost for linux) but cant find anything on usb HDD
I dont want to boot to this image, but if my system falls apart big time, i need to have an abc way to have it up and running again..


Im going to reformat my system with 64bit and drive encription, and well want a easy way to get my system back up if i cant fix an issue.

[/COLOR]

[COLOR="Navy"]
Cheers to the wise and helpful people out there making my change to linux such a smooth and "tell the world"  fan.[/COLOR]
:guitar:

---

### Post by wieman01 on 2007-10-29
Partimage is a good option. See signature.

---

### Post by scotthammy on 2007-10-29
[COLOR="DarkGreen"]Two issues with partimage

1. NTFS is not really supported.
2. How can i get it to show my USB HDD? 

do i need to mount usb or something?[/COLOR]

---

### Post by wieman01 on 2007-10-29
> **scotthammy said:**
> [COLOR="DarkGreen"]Two issues with partimage

1. NTFS is not really supported.
2. How can i get it to show my USB HDD? 

do i need to mount usb or something?[/COLOR]
1. NTFS is an issue and support for it is only experimental. FAT32 is generally no problem at all.

2. You need to mount it. See the tutorial for details.

---

### Post by scotthammy on 2007-10-29
Wishing to backup my windows NTFS system. so cant use partimage..

---

### Post by wieman01 on 2007-10-29
> **scotthammy said:**
> Wishing to backup my windows NTFS system. so cant use partimage..
You might want to use (Windows) Partition Magic instead to achieve just that. Did a great job for me on a couple of occasions. Or... you convert your current NTFS file system to a FAT32 one. That's easily done as well.

---

### Post by scotthammy on 2007-10-30
Sorry, maybe I didn&#8217;t make my intentions clear..

Current system: 
XP / Ubuntu Gutsy 32bit - working system. 

What I want to change:

Remove xp and reformat hdd as a blank and install 64bit Gutsy.

If for some reason I&#8217;m not happy with gutsy 64bit Only. I need a quick and easy way to ABC reimage my system back to "Gutsy32bit / xp" As well as MBR etc.

I also need to backup onto a USB HDD. 


I don&#8217;t really wish to just backup the windows partition, as I&#8217;m sure if I have a blank HDD and went to restore it, it would not work and or it would also be expecting the MBR and ubuntu 32bit etc.

a full drive image is the 100% no issue way. but allot of software will not support ntfs or windows software that has poor or no support for Linux etc.

:confused::)

---

### Post by FXEF on 2007-10-30
> **scotthammy said:**
> Sorry, maybe I didn&#8217;t make my intentions clear..

Current system: 
XP / Ubuntu Gutsy 32bit - working system. 

What I want to change:

Remove xp and reformat hdd as a blank and install 64bit Gutsy.

If for some reason I&#8217;m not happy with gutsy 64bit Only. I need a quick and easy way to ABC reimage my system back to "Gutsy32bit / xp" As well as MBR etc.

I also need to backup onto a USB HDD. 


I don&#8217;t really wish to just backup the windows partition, as I&#8217;m sure if I have a blank HDD and went to restore it, it would not work and or it would also be expecting the MBR and ubuntu 32bit etc.

a full drive image is the 100% no issue way. but allot of software will not support ntfs or windows software that has poor or no support for Linux etc.

:confused::)


You could use dd to clone to the USB drive. However, this is what I would do. Hard drives are rather cheap, so purchase a new hard drive. Replace the old drive with the new drive. Install the 64 bit OS on the new drive. If for some reason you need the 32 bit OS, just switch drives. Not any chance you will lose any data this way and most likely quicker.

You can install both 64 bit and 32 bit OS on same hard drive, they just need their own partition.

---

