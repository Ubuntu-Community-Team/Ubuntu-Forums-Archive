---
title: "trouble mounting"
date: 2008-01-07
forum: General Help
---

### Post by tralfas on 2008-01-07
ok so i have this 320gb sata hardrive. i partitioned 80gb and then put an ext3 file system on it. then i mounted it at /backup. this worked for a while then it started to give me and error like this ...

cannot mount volume 
unabel to mount the volume

details
mount_point cannot contain the following characters:newline, G_DIR_SEPERATOR(usually /)

i then would manually mount the drive everytime i wanted it then i decided to try and fix it for good and mounted the drive at /stuff instead. then i updated fstab. now i cant get it to work.

help please!:)

---

### Post by Scheater5 on 2008-01-07
That's a new one on me - but since it won't mount it at all, you can always make a dir in /mnt and put it there.  Sort of the "old skool" way.  Not very integrated, but it gets your data back.  
What kind of drive is it?  Sounds to me like there's some sort of bigger, underlying problem.  Possibly with linux, possibly with the drive.  I've had Windows-centric features of Western Digital drives cripple them over time.

---

### Post by tralfas on 2008-01-08
ill try mounting it on /mnt see if that works. i was looking around at my school and i saw that most of our macs had maxtor hard drives so i figured since macs are unix and maxtor can handle it why not linux. but yeah the drive is maxtor

---

