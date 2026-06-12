---
title: "Seagate HD not working?"
date: 2008-03-21
forum: General Help
---

### Post by angelinatoress on 2008-03-21
I have a Seagate 160GB SATA Internal Hard Drive and I decided to make it external, so I can swap it between my laptop (Ubuntu 7.04) and this computer.  So I bought a [Bytecc ME-747SU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817145047").

Well, the hard drive is working as I checked it on my girlfriends Windows Laptop and it mounts up and is displayed in "My Computer" (Vista Home Premium 32bit).

But when I went to put it on my Linux (Ubuntu 7.04) Desktop, it is not mounting at all.  I did an fdisk -l to see if it is there, and it is.  I am just at a loss of what to do next, all the other times, my externals mount no problem.  This is just being hairy.

Results of the fdisk -l:
```
angel@desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23849   191567061   83  Linux
/dev/sda2           23850       24321     3791340    5  Extended
/dev/sda5           23850       24321     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7297    58613121   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table
angel@desktop:~$ 
```
Anyone know what to do next?  Any and all help is greatly appreciated.  Thanks.
All I probably have to do is format it to get it to mount, but I forgot where to do this at as I haven't formatted a hard drive since 7.04 came out.

---

### Post by InvIsiBlekID on 2008-03-21
Yea, I would re-format the drive.  Gparted should do it for you.
```
sudo apt-get install gparted
```

---

### Post by angelinatoress on 2008-03-22
I installed gparted and let it run it's course.  I turned off the hard drive enclosure afterwards, then I turned it back on.  It now shows up in "Computer".  At first I couldn't do anything to it unless I was in sudo, but I changed that.  Now I can't rename the drive to what I want.  In "Computer" it says "149.0 GB Volume: disk-1".  But I wish to change it to "Multimedia".  But for some reason I can't.  When I do try, it pops up with:

"**The item could not be renamed**"
Sorry, couldn't rename "149.0 GB Volume: disk-1" to "Multimedia".

Any clue on how to change it?

---

### Post by angelinatoress on 2008-03-25
*Bump*

---

### Post by tgalati4 on 2008-03-25
>sudo e2label /dev/sdc1 Multimedia

---

### Post by angelinatoress on 2008-03-26
Doesn't work.  Still remains as "149.0 GB Volume: disk".  That's even after doing it, rebooting both my computer and the hard drive.

---

