---
title: "Trying to change Internal HD Label"
date: 2018-06-12
forum: General Help
---

### Post by heroquestelf on 2018-06-12
Before I start, I am running Ubuntu MATE 18.04 LTS on a Dell Inspiron with a 3.2 GHz processor

 
 
 I’m trying to re-name the secondary hard drive on my computer and I can’t figure out how to do it. It is an internal 1 TB drive and it’s formatted with Ext4.
 
 
 I’ll start with the disk label. I would like the label on the disk to read “business”. Instead, it’s currently listed as either “999 GB Volume” per the desktop icon, or when you pull it up using nautilus, it is identified by it’s UUID, which is ac70637d-32fb-4fe4-93a6-130b44910b1a --(which I am totally not typing again and from here forward will just use ***UUID***.)

 
 
 When I do a sudo nautilus, it pulls up by the UUID, and when I try to change the disc label, it gives me the following error:

 
 
 Sorry, could not rename “*UUID*” to “Business”: Error renaming file /media/jonathan/*UUID*: Device or resource busy.

 
 
 I tried unmounting it first, but when I unmount it the computer no longer sees it, so I can’t figure out how to rename it.

---

### Post by Holger_Gehrke on 2018-06-12
Unmount the device and In a terminal enter```
sudo tune2fs -L business UUID=ac70637d-32fb-4fe4-93a6-130b44910b1a
```

Holger

---

### Post by deadflowr on 2018-06-12
```
sudo tune2fs -L label-name-here /dev/sdXx
```
Change label-name-here to whatever you want the label to be and change sdXx to the disk and partition numbers.

ninja'd

---

### Post by heroquestelf on 2018-06-12
[IMG]http://dunboyneathleticclub.com/wp-content/uploads/2016/09/Thank-You-PNG-800x500_c.png[/IMG]
[SIZE=5]You guys are freaking **AMAZING.**[/SIZE]

---

