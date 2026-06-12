---
title: "[SOLVED] Partition name weirdness!"
date: 2006-11-02
forum: General Help
---

### Post by vyruss on 2006-11-02
Hi, I just upgraded from Dapper to Edgy.
I have always had 4 data partitions mounted from /etc/fstab:
```
/dev/hda1 (NTFS)  as /media/hda1
/dev/hda5 (FAT32) as /media/hda5
/dev/hdb1 (EXT3)  as /media/hdb1
/dev/hdb5 (FAT32) as /media/hdb5
```And they always appeared as four icons on my desktop. However, **after the upgrade**, I get the strange behaviour shown in the screenshot attached:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18722&d=1162448460[/IMG]

**/dev/hdb5** is now assigned a peculiar, unreadable name!

Does anybody have any ideas?

Cheers!

---

### Post by dcstar on 2006-11-02
> **vyruss said:**
> 
.......
**/dev/hdb5** is now assigned a peculiar, unreadable name!

Does anybody have any ideas?

Cheers!

I believe Edgy now tries to use the filesystem partition label to assist you in identifying the partition (rather than just a hardware designation).

Looking at your problem, it seems to be a partition label that isn't being handled 100% correctly.

There may be a way to turn it off, hopefully someone else can help you with this.

---

### Post by vyruss on 2006-11-03
bump? :( (sorry)

---

### Post by CatKiller on 2006-11-04
This came up in a different thread, and the poster found that by booting into Windows and changing the volume label, the problem went away. If you're dual-booting, that's probably the easiest. I don't yet know how to change the label in Linux.

---

### Post by noynac on 2006-11-04
> **CatKiller said:**
> This came up in a different thread, and the poster found that by booting into Windows and changing the volume label, the problem went away. If you're dual-booting, that's probably the easiest. I don't yet know how to change the label in Linux.

Yeah, I had this same problem and someone suggested that I rename the volume label in windows. This worked, although the volume label is now all caps (not a biggy). I spent a lot of time searching various forums but never found an answer why this was happening.

BTW, in my case, and apparently in yours, the volume that had a problem was Fat32, so I assume this is relevant in some way.

---

### Post by razahel on 2006-11-06
Hi,

I ran into the same problem with a fat32 partition.
The only thing which helped was to rename in under windows.

regards razahel

---

### Post by vyruss on 2006-11-06
> **razahel said:**
> Hi,

I ran into the same problem with a fat32 partition.
The only thing which helped was to rename in under windows.

regards razahel

Well, I never *ever* want to boot into windows again, so what I did was this:

I installed **mtools** and used it to change the volume label. Sure enough, it worked, but now instead of /dev/hdb5 I can see the volume name. Oh well, I guess clearing the volume label might work :) Thanks guys!

---

### Post by shane2peru on 2007-02-24
> **vyruss said:**
> Well, I never *ever* want to boot into windows again, so what I did was this:

I installed **mtools** and used it to change the volume label. Sure enough, it worked, but now instead of /dev/hdb5 I can see the volume name. Oh well, I guess clearing the volume label might work :) Thanks guys!

Ok, this is an old thread, but I would love some clarification on this.  I too have always not liked this.  I have before gone into windows and reset the name of the partition, or USB stick etc.  However I want to know how to do this in Linux, and not have to lean on Windows every time to do this.  Can anyone clarify this **mtools** stuff.  I'm really interested in figuring this out.  Also what is the risk factor?  Thanks!

Shane

---

### Post by vyruss on 2007-03-09
> **shane2peru said:**
> Ok, this is an old thread, but I would love some clarification on this.  I too have always not liked this.  I have before gone into windows and reset the name of the partition, or USB stick etc.  However I want to know how to do this in Linux, and not have to lean on Windows every time to do this.  Can anyone clarify this **mtools** stuff.  I'm really interested in figuring this out.  Also what is the risk factor?

Here you go: 

[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

---

### Post by vyruss on 2007-03-12
For anyone interested in this, here's the bug I filed:

[https://launchpad.net/bugs/69914](https://launchpad.net/bugs/69914)

---

### Post by shane2peru on 2007-03-13
> **vyruss said:**
> Here you go: 

[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

Hey Thanks vyruss!  I will have to try it as soon as I get my computer back!  I read over it and it looks pretty simple.  Have you successfully done this as well?  

Shane

---

### Post by vyruss on 2007-03-14
> **shane2peru said:**
> Hey Thanks vyruss!  I will have to try it as soon as I get my computer back!  I read over it and it looks pretty simple.  Have you successfully done this as well?  

Shane

Yeap, it works :)

---

### Post by shane2peru on 2007-03-14
Great when I get my computer back I will be trying that!  THanks again.

Shane

---

