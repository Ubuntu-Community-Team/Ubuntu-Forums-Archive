---
title: "Available shrink size is shrinking!"
date: 2008-02-01
forum: General Help
---

### Post by shoeboxin on 2008-02-01
So, I've installed ubuntu and other OS's on my laptop harddrive and have always done it by partitioning. I've used both the Windows partitioner and the built in Ubuntu partitioner. What I've noticed is that after I delete a partition, if I go to create a new one, the "available shrink size" is lower. For example, on my 120 gb HD I have 61 gb of free space, however if I try to shrink the drive, the "max available shrink" is only 20 gb. And again, every time I delete a partition and extend my main one, I don't really get the space back. Any suggestions? Windows says it could be because pagefiles or snapshots are enabled, but I don't know how to remove those.
Thanks a lot for any help.

---

### Post by shoeboxin on 2008-02-03
Anybody have an idea?

---

### Post by NightwishFan on 2008-02-03
The solution is to defragment the hard drive that should gain your shrink space back. You can squeeze a bit more by disabling the pagefile but it seems to make little difference. Please tell me if my solution works out for you.

---

### Post by shoeboxin on 2008-02-04
> **NightwishFan said:**
> The solution is to defragment the hard drive that should gain your shrink space back. You can squeeze a bit more by disabling the pagefile but it seems to make little difference. Please tell me if my solution works out for you.

Thanks, however after defragmenting there was no change in the available shrink space. Any other ideas?

---

### Post by NightwishFan on 2008-02-04
You need to likely use a more efficient defragmenter program i had the same problem when i wanted to free 100gb for my ubuntu partition. After a defrag it enabled me to free as much space as i wanted (110gb of my 177gb hd)

The shrink will remove as much as it can until it hits an unmovable system file. Find a defrag program that can move these system files.

---

### Post by shoeboxin on 2008-02-04
Actually...I tried using DiskKeeper 2008 and that didn't change anything. I defragged using the normal program as well as before windows booted. It didn't change the available shrink space one bit. What else could be keeping me from this space? What do deleted OS's leave behind that is taking up so much space?

---

### Post by NightwishFan on 2008-02-04
I had used diskkeeper as well just be sure you did the system files and it should allow more shrink space. Im not sure what other steps you can take.

---

### Post by shoeboxin on 2008-02-04
I even tried O and O disk defragmenter. Although it gave me more space on my HD, it did not increase the available shrink size in the windows partitioner...I'm running Vista if anyone cares to know, and I've had Ubuntu running, but would like to figure out this available space issue before installing again.

---

### Post by shoeboxin on 2008-02-06
Anyone else have an idea?

---

### Post by NightwishFan on 2008-02-06
[http://ubuntuforums.org/showthread.php?t=534711]("http://ubuntuforums.org/showthread.php?t=534711")

This is a thread about your problem. The defragmenting , if done correctly should be the answer. Also they mentioned the virtual page, which made a minor difference for me. You can also try the gparted live cd.

---

