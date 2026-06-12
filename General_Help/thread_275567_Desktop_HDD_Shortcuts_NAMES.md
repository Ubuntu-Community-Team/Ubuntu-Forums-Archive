---
title: "Desktop HDD Shortcuts NAMES??"
date: 2006-10-11
forum: General Help
---

### Post by becatlibra on 2006-10-11
New 6.0.6.1 Install.  Not my first Ubuntu install and definately not my firs t linux install.

So

There were icons on my desktop for the 3 windows partitions I have.  One is the C drive, One is a Service Partition from IBM that happens to be fat32 and the Third is a partition I set up for Linux and Windows to share.

Long story shorter, I modified my fstab to get rid of the service partition and changed the mount point of the shared partition from /share to /media/hda3.

Now the HDD icon is on the desktop however it is named hda3 whereas the C drive (which is HDA1) is named IBM_PRELOAD.

Where are these names stored?  Where can I change them?

Thanks

B

---

### Post by TLE on 2006-11-12
I would really like to know the answer to this one also. Lets hope someone answers.

---

### Post by pingvin on 2006-11-12
Dapper Drake - 6.06.1

If anyone has any info on this it would be much appreciated. I too have a shared vfat partition, mounted at '/media/windows' and one day, having been running windows that day, I booted into Ubuntu, and the Gnome desktop icon had changed its name from 'windows' to '0'. The only thing I'd done that day was to defragment the partition in windows. It's stayed as '0' ever since.

Thanks in advance,

Mike

---

### Post by dcstar on 2006-11-13
> **becatlibra said:**
> 
.........
Now the HDD icon is on the desktop however it is named hda3 whereas the C drive (which is HDA1) is named IBM_PRELOAD.

Where are these names stored?  Where can I change them?

Thanks

B

They are partition labels, do a forum search for changing the labels on non-DOS/Windows partitions, and using the native Windows is best for changing those names.

My USB stick appears on my desktop with the EXT2 label I gave it.

---

