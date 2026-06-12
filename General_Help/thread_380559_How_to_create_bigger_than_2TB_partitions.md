---
title: "How to create bigger than 2TB partitions?"
date: 2007-03-09
forum: General Help
---

### Post by sicofante on 2007-03-09
Is there a way to create partitions bigger than 2 terabytes in Ubuntu? I can use both 32 and 64 bit versions.

Thanks for any help.

---

### Post by jholzman on 2007-05-14
I just bought a 10TB RAID.  I need this too.  I am looking at lvm2 tools.  Not sure how to use it yet.

---

### Post by psusi on 2007-05-14
Yep... use LVM.  The MSDOS partition table can't see beyond 2 TB.

---

### Post by sicofante on 2007-05-16
I discovered that partitions labeled GPT can go far beyond the 2TB limit of MSDOS labeled partitions, so just go inside Gnome Partition Editor and set the label for your array to GPT. Then you'll be able to create your big partitions.

Absolutely no need to use LVM.

---

### Post by psusi on 2007-05-16
I suppose GPT will work too, but if you have THAT much storage, you probably want lvm for other reasons ;)

---

### Post by sicofante on 2007-05-16
Like what? (Honestly interested)

I tend to think LVM adds a layer of complexity and that you should use it mainly to build software arrays of a number of different disks. I've understood the 10TB array in question has it's own hardware RAID setup, that the system sees this RAID array as just one big disk and so I don't quite see the need for LVM.

---

### Post by aldenhg on 2007-05-16
How about XFS? I don't know much about it, but I do know that it can be used for gigantic partitions - something on the order of 8 exabytes. That's a lot of bytes. Check out the wikipedia page here: [http://en.wikipedia.org/wiki/Xfs](http://en.wikipedia.org/wiki/Xfs)
If you want to make an XFS partition, Gparted should be able to do it for you through the usual motions. If that doesn't work, try the Gparted LiveCD. It can be found here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Good luck!

---

### Post by sicofante on 2007-05-17
XFS is a filesystem type. That's a whole different thing. You can't creat bigger than 2TB XFS partitions on a disk (or RAID) labeled "MSDOS". You must label it GPT first, then you can create any type of partition, including, of course, XFS.

BTW: LVM won't solve the issue of >2TB partitions.

Here's some interesting reading: [http://www.unixgods.org/~tilo/larger_2TB.html](http://www.unixgods.org/~tilo/larger_2TB.html)

---

