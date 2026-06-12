---
title: "Getting HAL to use noatime by default"
date: 2008-04-16
forum: General Help
---

### Post by Erin on 2008-04-16
Hello,

Where does the information reside to force HAL to mount my USB stick using "noatime" as a mount option? I've tried searching these forums and using Google but nothing seems to answer what I am after. Basically, I just need to know where the config file is stored. 

I happen to be using Hardy with a Gnome desktop but gnome-mount seems not to offer any options within Nautilus to do anything different. I am at a loss.

TIA, Erin.

---

### Post by kerry_s on 2008-04-16
in terminal:
type> sudo updatedb
locate hal
or
whereis hal
or
find hal

but why would you need to mess with it, it don't really matter on a external, especially if it's formatted fat.

---

### Post by Erin on 2008-04-17
> **kerry_s said:**
> in terminal:
type> sudo updatedb
locate hal
or
whereis hal
or
find hal

but why would you need to mess with it, it don't really matter on a external, especially if it's formatted fat.


Thanks for the reply but I am after the relevant config file as I have tried various searches but to no avail. The reason is to minimise writes to a USB stick (as they have a limited life span based upon write cycles). "gnome-device-manage" shows noatime is an option but I need to know in which file to insert it as the "mtab" entry is dynamic.

Erin

---

### Post by kerry_s on 2008-04-17
noatime is a system setting, it does nothing to the usb drive. 
there's no writing to the drive unless you change something on the drive, otherwise it's only read. you'll get no performance gain and there's no effect on the life span of the drive.

the best way to see where hal is installed is to look in synaptic.
open synaptic> click status(left,bottom,corner)> installed, highlight any line by clicking on it, start typing hal, right click on hal> properties> installed

that will tell you where everything hal installed is.

i can't tell you where, cause i don't have hal->

---

### Post by Erin on 2008-04-17
> **kerry_s said:**
> noatime is a system setting, it does nothing to the usb drive. 
there's no writing to the drive unless you change something on the drive, otherwise it's only read. you'll get no performance gain and there's no effect on the life span of the drive.

the best way to see where hal is installed is to look in synaptic.
open synaptic> click status(left,bottom,corner)> installed, highlight any line by clicking on it, start typing hal, right click on hal> properties> installed

that will tell you where everything hal installed is.

i can't tell you where, cause i don't have hal->

You are totally missing the point. I have HAL, I need to modify the configuration of HAL. What you've written is totally incorrect as USB memory sticks have limited lives based on write cycles.

> Linux has a special mount option for file systems called noatime that can be added to each line that addresses one file system in the /etc/fstab file. If a file system has been mounted with this option, reading accesses to the file system will no longer result in an update to the atime information associated with the file like we have explained above. The importance of the noatime setting is that it eliminates the need by the system to make writes to the file system for files which are simply being read. Since writes can be somewhat expensive, this can result in measurable performance gains. (from [http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec73.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec73.html)).

---

### Post by kerry_s on 2008-04-17
your not getting the point, it doesn't work that way with usb.
the drive is read into buffer, any reading you do comes from buffer, not from the drive.
i know what noatime is i use it on my system.

i've told you how to use synaptic to find where all hal files are installed. you can do as you wish, it's your system.

---

### Post by Erin on 2008-04-18
Does that explain why eeeXbuntu state to ensure noatime is used then? Or most of the other data I've seen regarding USB devices and shortening of their life by excessive write cycles? Oh no, of course not, it is just me deing a dullard...!

Read what I write. It is about data being written to a USB device not read. Buffers are irrelevant as the quote I posted states there are performance gains and additionally, I've tried the synaptic route but it didn't prove useful hence why I ask the question. Please, if you cannot give a direct answer akin to; "you need to edit <this> file", then do not bother replying.

---

### Post by dcstar on 2008-04-18
> **kerry_s said:**
> your not getting the point, it doesn't work that way with usb.
the drive is read into buffer, any reading you do comes from buffer, not from the drive.
i know what noatime is i use it on my system.


The standard "atime" function - for filesystems that use it - **writes** a timestamp entry whenever a file is accessed, so it certainly does cause more device writes whenever it is utilised.

"noatime" will reduce writes, as well "nodiratime" which stops a similar update when directory entries are accessed.

Here is something that may help the OP:

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by kerry_s on 2008-04-18
:lolflag:
yeah, that should give that usb a extra 1000 writes. usb's are so cheap these days and getting cheaper. most will lose there drives before it even comes close to the end of it's life. is it really worth it?

---

### Post by Erin on 2008-04-18
> **dcstar said:**
> The standard "atime" function - for filesystems that use it - **writes** a timestamp entry whenever a file is accessed, so it certainly does cause more device writes whenever it is utilised.

"noatime" will reduce writes, as well "nodiratime" which stops a similar update when directory entries are accessed.

Here is something that may help the OP:

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

David, 

Exactly what I was after. Thanks for your help. Much appreciated.

E.

---

