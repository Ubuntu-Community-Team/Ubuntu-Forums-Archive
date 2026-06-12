---
title: "Partition stays full"
date: 2007-10-30
forum: General Help
---

### Post by Dooley on 2007-10-30
Hey there,
 I have a separate partition on my laptops hardriive that is 21gbs big, its just there for media files and project backups etc.
I have about 10gbs of files on it, Ive checked this with filelight, but when I run df -h on linux declares its full.
I've no idea why, is there any way for linux to "check" the partition and detect how much free space is on it.

Cheers in advance

---

### Post by taurus on 2007-10-30
Is that partition part of your $HOME?  Which partition is it from this output?

```
df -h
```

---

### Post by Dooley on 2007-10-30
Its my /dev/sda1. 
It used to be a window partition but I got rid of windows and just put files on it.
The only other partition is my root which is /dev/sda2.

---

### Post by taurus on 2007-10-30
Can you post?

```
df -h
du -h /media/sda1 <-- I assume you mount /dev/sda1 to /media/sda1.
```

---

### Post by Dooley on 2007-10-30
df -h relating to the hard drive in question is:

/dev/sda1        21G     20G        137M     100%    /media/sda1

du -h seems to show all my files on the partition I have a few eclipse workspaces up there so there is LOADs of files probably not worth showing up here.

Sorry my laptop isnt on the wireless network here so im typing all this stuff out.

---

### Post by taurus on 2007-10-30
But did it report about 20GB of total space used up at the end, after listing all the directories?

---

### Post by EriktheUnready on 2007-10-30
ne hidden files? ls -la maybe?
what filesystem is it?

---

### Post by Dooley on 2007-10-30
Hmm you're right it does say 20G of files used.

---

### Post by taurus on 2007-10-30
It will tell you how much space each directory is taking up so you need to look at them by hand.

---

### Post by gobuntu on 2007-10-30
> **Dooley said:**
> df -h relating to the hard drive in question is:

/dev/sda1        21G     20G        137M     100%    /media/sda1

du -h seems to show all my files on the partition I have a few eclipse workspaces up there so there is LOADs of files probably not worth showing up here.

Sorry my laptop isnt on the wireless network here so im typing all this stuff out.

Hi Dooley,

When you say "got rid of windows" it all depends on how you did that.

In particular, it is quite difficult to get rid-of some Eclipse directories and/or files in Windows.

Just removing directories or click delete does not quite do it.

It might be necessary to format the partition, after you have data you want somewhere else.

---

### Post by Dooley on 2007-10-30
Cheers thats a great help. 

:D

---

