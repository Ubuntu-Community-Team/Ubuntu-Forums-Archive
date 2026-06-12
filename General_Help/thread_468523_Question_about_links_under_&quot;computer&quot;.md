---
title: "Question about links under &quot;computer:///&quot;"
date: 2007-06-08
forum: General Help
---

### Post by Laptop_Max on 2007-06-08
I'm wondering if its possible to change the name of the links under "computer:///"  I have an extra hard drive I just recently added to my system and under "computer:///" its listed as: ( 149.0 GB Volume: disk )  The drive is going to be for file storage and I would like to give it a descriptive name, maybe "Storage" or something similar, the name provided is just not going to cut it  I need other users to have some kind of clue as to where to find things.  Is there a way I can go about doing this?


Also In the same area I have "Floppy 1" and "Floppy Drive", I have no idea why there are two of them.  It won't let me remove one of them...

---

### Post by Laptop_Max on 2007-06-10
No one knows how to go about doing this?  If I didn't make myself clear enough and you don't understand what I'm trying to do let me know and I will try to explain better, and if its not possible please tell me.....

---

### Post by zekopeko on 2007-06-10
what is the filesystem on it? ext3 or some other?

---

### Post by tpg on 2007-06-10
This link could be useful:
[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/]("http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/")

---

### Post by zekopeko on 2007-06-10
or for ext2/3 the command should be e2label

---

### Post by tpg on 2007-06-10
Or for ntfs, ntfslabel.

---

### Post by Laptop_Max on 2007-06-10
The filesystem is reiserfs just so you know, and i'm going to look over the link about mtools.

---

### Post by Laptop_Max on 2007-06-10
Ok, I have it all under control now.  I used reiserfstune to add a label to the device, rebooted, and it now shows up as "Storage" instead of 149.0 GB Volume: Disk

Anyone have a clue on why I have 2 floppy entries when I only have 1 floppy drive?

---

