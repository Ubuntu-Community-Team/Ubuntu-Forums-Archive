---
title: "How do I install ubuntu in a new notebook which is loaded with DOS?"
date: 2015-01-15
forum: General Help
---

### Post by arroy_0209 on 2015-01-15
I have purchased a notebook in which DOS is already loaded and no other OS is present. In fact during boot I get an option to select one out of three modes of DOS (with maximum ram etc).  How do I install Ubuntu in it? Will I have to remove DOS first and then install Ubuntu or should I keep DOS as it is (but then probably at each boot I will be asked to select Ubuntu or dos which I  don't want). Also this nebook doesn't have cd drive. Please suggest how I should proceed.

 In case removal of dos is appropriate please suggest how to do that.

---

### Post by kerry_s on 2015-01-15
you need a usb installer of ubuntu. i suggest have a friend help you with that.
this is 1 of those barebones notbooks right? not 1 of those old school third world recycled notebooks you've snagged off ebay? 
specs?

---

### Post by arroy_0209 on 2015-01-15
This netbook is new, declared to be manufactured in September,2014 in China by Asus. Fact is I purchased from online store but never suspected that they sell recycled goods. A little more clarification from you will be helpful. I purchased this because most other variants come with Windows which I dislike. The specs in brief: 11.6inch, corei3 4010U processor, 4gb ram, 500gb hdd. Tell me if further information is needed. Since this is my first purchase from online store, I will be grateful if you could tell if this is really a  recycled product.

---

### Post by QIII on 2015-01-15
Asus (the last four letters of "Pegasus") is a Taiwanese company, so "Made in China" is legit.  Don't worry about it.

---

### Post by sudodus on 2015-01-15
Since the computer is delivered with DOS, I think the idea is that it should be possible (or should I say not intended to be difficult) to install an operating system. You find a lot of information about booting and installing from a USB pendrive at the following links and links from those links.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by kerry_s on 2015-01-15
lol, those are great specs sounds like it would be the perfect linux setup. just find someone who has a working os, install unetbootin & make you a usb installer. boot from the usb & just follow the directions on the screen.

i once had a friend give me a dos computer, this thing was from the 80's, can't believe dos is still around, i think i still have some dos floppys somewhere in the house.

---

### Post by sudodus on 2015-01-15
> **kerry_s said:**
> lol, those are great specs sounds like it would be the perfect linux setup. just find someone who has a working os, install unetbootin & make you a usb installer. boot from the usb & just follow the directions on the screen.

i once had a friend give me a dos computer, this thing was from the 80's, can't believe dos is still around, i think i still have some dos floppys somewhere in the house.

+1

Unetbootin is a good tool with versions for linux, Windows and MacOS.

I recommend an Ubuntu flavour of the version 14.04.1 LTS (long time support).

---

### Post by arroy_0209 on 2015-01-15
But I still can't decide about the existing DOS. Should it be 
 left  as it is now? Or should it be removed first? How do I remove it, in case you suggest to do so.

---

### Post by sudodus on 2015-01-15
In the Ubuntu install drive (that you make by burning or flashing the Ubuntu iso file into a DVD disk or USB pendrive), there is a program called ***gparted***. You can use it to edit partitions (change, remove, create) in the internal drive. You can use it to either leave the DOS system or shrink its partition or completely remove it. 

Run it from a ***menu*** or from ***dash*** or from a terminal window ```
sudo -H gparted
```

See these links

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I would leave the DOS system, but with a rather small partition (unless you want to play DOS games, in that case you may need a little more drive space for it, but still less than linux). But on the other hand, it is free software like Ubuntu and most other linux distros, so if you remove it, you can easily download it and and install it again.

---

### Post by Yellow Pasque on 2015-01-15
I would try and keep the DOS partition as well, if only until the warranty runs out. Otherwise, the vendor could pull the old, "That's not the OS it came with. No support for you!" trick even if it's a hardware issue.

---

