---
title: "Increasing HD Size"
date: 2006-12-12
forum: General Help
---

### Post by wireddad on 2006-12-12
I current have a dual boot system, WindowsXP and Ubuntu Edgy.  Is it possible to increase the size of the Ext3 without messing anything up?  If so, how?  Thanks.

---

### Post by Hurons on 2006-12-12
yes it is... GPARTED is a linux disto that works well.
Its a live cd that is very user friendly.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)


This is the tool I use.

---

### Post by wireddad on 2006-12-12
I will give GPart a read.
 
I will need to delete part of the windows partition.  Then add the free space to Ext3.  Still can be done?
 
"This is useful for creating space for new operating systems, reorganizing disk usage, copying data residing on hard disks and mirroring one partition with another (disk imaging)."
 
From reading this quick excerpt, it SOUNDS like it will not damage any data.  Right?

---

### Post by earobinson on 2006-12-12
gparted is the way to go, and if your going to be using any partitions in use you will need the ubuntu live cd to edit the partitions, also some people report problems with the ubuntu live cd and gparted in that case I recommend [http://www.google.ca/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=9M9-RajwFZXQgQL9m-nZCA&usg=__RmAG9QoJzpUqjZlvO99ie24OQlw=&sig2=vI-RoQhHr-jC8qcCEGesXQ](http://www.google.ca/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=9M9-RajwFZXQgQL9m-nZCA&usg=__RmAG9QoJzpUqjZlvO99ie24OQlw=&sig2=vI-RoQhHr-jC8qcCEGesXQ)

---

### Post by wireddad on 2006-12-12
> **earobinson said:**
> gparted is the way to go, and if your going to be using any partitions in use you will need the ubuntu live cd to edit the partitions, also some people report problems with the ubuntu live cd and gparted in that case I recommend [http://www.google.ca/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=9M9-RajwFZXQgQL9m-nZCA&usg=__RmAG9QoJzpUqjZlvO99ie24OQlw=&sig2=vI-RoQhHr-jC8qcCEGesXQ](http://www.google.ca/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=9M9-RajwFZXQgQL9m-nZCA&usg=__RmAG9QoJzpUqjZlvO99ie24OQlw=&sig2=vI-RoQhHr-jC8qcCEGesXQ)
 
 
I'd just checked out the link quickly.  It does say that it is a Live CD version of GPart?

---

### Post by smoker on 2006-12-12
> **wireddad said:**
> I'd just checked out the link quickly.  It does say that it is a Live CD version of GPart?

yes, download and burn to disk, and set computer to boot from cd first.

remember to clean the junk from your windows partition and defrag it before resizing it. it is also wise to backup important data,

good luck

---

### Post by wireddad on 2006-12-12
> **smoker said:**
> yes, download and burn to disk, and set computer to boot from cd first.
 
remember to clean the junk from your windows partition and defrag it before resizing it. it is also wise to backup important data,
 
good luck
 
Thanks.  Will try.

---

