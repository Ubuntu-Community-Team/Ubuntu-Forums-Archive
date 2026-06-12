---
title: "Which Option Do I Chose?"
date: 2007-07-10
forum: General Help
---

### Post by StephanGFX on 2007-07-10
On the tutorial to dual boot Linux and XP, it tells you to put the following as your default setting. 

[http://apcmag.com/system/files/images/xp_ubuntu_07.preview.jpg](http://apcmag.com/system/files/images/xp_ubuntu_07.preview.jpg)

but I'm not sure what that will do. Can anyone explain? Will it delete any of the files I have?

---

### Post by scragar on 2007-07-10
no, by default you have 1 partition, using up all of your hard-disk, that only has windows on it.
This option takes some of the space windows isn't using(and nothing else is using as well) and resizes the partition so that free space can be used to install linux.

windows and all the files already on your computer stay.

---

### Post by jaytek13 on 2007-07-10
Option 1 will reorganize your windows partition to make room for Ubuntu. While it is generally speaking safe, data loss is a possibility.

Option 2 would erase the entire disk and everything on it and then install Ubuntu.

Option 3 is similar to option 1 yet it won't reorganize any of the files.

Option 4 is for advanced users who would like to specify the sizes of their /, swap, and home directories. Generally there's no reason to fiddle around with this.


You should probably just choose option 1.

---

### Post by davidjmayo on 2007-07-10
Hope this isn't too late

If you do option 1 before you do it then do this:

Defragment your windows a few times (this will minimise,** not guarantee** that there will be no data loss or corruption)
Backup your data to be safe

Install with option 1

---

