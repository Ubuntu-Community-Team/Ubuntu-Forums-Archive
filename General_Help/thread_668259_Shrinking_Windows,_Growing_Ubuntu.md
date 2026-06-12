---
title: "Shrinking Windows, Growing Ubuntu"
date: 2008-01-15
forum: General Help
---

### Post by amtur_poet on 2008-01-15
I have a 178 GB windows vista partition that I want to shrink to add more room for ubuntu. Apparently, I can't do this in Gparted, since it won't let you edit NTFS partitions. Is there any other program I can use to resize the partitions? Or just another method?

---

### Post by meindian523 on 2008-01-15
Windows Vista partitions are best messed with with the Vista Disk Management utility itself,since resizing by 3rd party utilities result in loss of data,it's oftentimes been seen.Simply,defrag your Vista partition about 2-3 times and go ahead with resizing.You can "grow" your Ubuntu partition with GParted.

---

### Post by amtur_poet on 2008-01-15
Thanks; I'll try that, then post the results.

---

### Post by amtur_poet on 2008-01-15
Okay, let me start by explaining that my ubuntu partition is not formatted. It is unallocated space. I set up 20 gigs of more unallocated space, but I don't know how to merge the original ubuntu space with the new space. How can I do that?

---

### Post by logos34 on 2008-01-15
Download the Gparted live cd.

Read this
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by meindian523 on 2008-01-16
Since you have not yet installed Ubuntu,you can just create a extended partition which occupies your "new" 20 gigs AND the "old" unallocated space you had set aside for Ubuntu.

---

### Post by amtur_poet on 2008-01-16
No, I have installed Ubuntu, but I used the Wubi installer, and the partition was treated as unallocated space as opposed to an actual Linux partition. How would I combine both the partitions of unallocated space, without uninstalling ubuntu? I think that if I make them both into a new partition, it will erase them.

---

### Post by logos34 on 2008-01-16
Boot fro the ubuntu live cd and post a screenshot of Gparted if you could.

system>admin>gnome partitiion editor

---

### Post by amtur_poet on 2008-01-16
Here's the screenshot. Ubuntu is installed on the first block [10 GB unallocated space]. Once again, I have already installed Ubuntu.

EDIT: After checking the space's properties, I found that the space Ubuntu is installed on is called a "rootfs" partition.

---

### Post by logos34 on 2008-01-16
First of all, wubi does not install ubuntu on a separate partition; ubuntu is installed *inside *windows partition as a loopmounted filesystem. So either continue to run linux as is, but expand the vista partition, or shift linux to its own, permanent partition--either using the [LVPM method]("http://lubi.sourceforge.net/lvpm.html"), or do a fresh install.

Secondly, you can't combine two noncontiguous, unallocated regions.  What you'll have to do is  resize the windows partition.  This is best done with Vista's built-in Disk Management utility.  I recommend you first grow vista to the front of the disk.  Then go ahead with LVPM or reinstall in the remaining disk space.

---

