---
title: "Name of mounted partitions on desktop"
date: 2008-04-30
forum: General Help
---

### Post by amaroKer on 2008-04-30
I have an external hard drive with no volume label, and a memory key labeled 'TRAINWRECK'.

When plugged in, the memory key appears on the desktop with the name TRAINWRECK, and mounts to /media/TRAINWRECK.  This is with no configuration.

The external hard drive mounts to /media/misery because I told it to under the "Volume" tab in properties.  The desktop name, however, is "107.4 GB Media".

If no mount point is specified under the "Volume" tab, Gutsy would name the icon "disk", where Hardy calls it "107.4 GB Media".  Both would mount it under /media/disk.

It appears that Hardy names the desktop icon according to the actual volume label (and if none, defaults to the size of the volume), where Gutsy would name the icon according to its mount point under /media.

I would like to configure Hardy to behave in this manner.  Any ideas?

---

### Post by jcpeart on 2008-05-04
I would like help with this also. I am running 3 250 GB hard drives and it is disconcerting to have them labeled on the desktop and in nautilus as: "208 GB Media" and "236 GB Media".
 It is downright confusing.

Jim

---

### Post by gnivler on 2008-05-06
I am not familiar with a way to do what amaroKer outlined, but this post has information on labelling NTFS (and other FS) partitions so at least the drive icons will have names:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

It's about half way down, you could search for "How to Label", with different file systems outlined very clearly.  Thanks to bodhi.zazen for the post.  Also worth saying the post is a trove of other information.

---

### Post by Ziggy72 on 2008-05-06
I find that all my partitions, when mounted in Hardy, display their label names. My suggestion is to open Gparted and try giving appropriate label names to your partitions. I don't know if this will work for ntfs partitions - if not, you'll have to give the partition(s) their label names when in Windows. However, Gparted label editing should certainly work for other file systems.

---

### Post by amaroKer on 2008-05-07
That is a workaround that I have considered.  Thank you for your replies.

I have picked through GConf trying to find a key that will change this behavior, but to no avail.  I'm thinking that I won't mark as solved until I find how to change that.  It has to be possible, because it has changed from 7.10.

---

### Post by Tares on 2008-05-08
This workaround doesn't work for my reiserfs partitions :/ Anyway i would be glad if there was a way to restore the behavior of mounted drivers like it was in 7.10, I mean,  to show only on desktop drives that are mounted in /media/

---

### Post by jcpeart on 2008-05-11
I solved the situation on my ext3 system by setting the disk label as recommended using the tune2fs command:

sudo tune2fs -L NewName /dev/sdx1

then a reboot and the new label name appears on the desktop as opposed to the "733 GB Volume" designation.

:)

---

