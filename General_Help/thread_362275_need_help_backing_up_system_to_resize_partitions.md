---
title: "need help backing up system to resize partitions"
date: 2007-02-15
forum: General Help
---

### Post by harty83 on 2007-02-15
I have a hard disk that is partitioned as follows:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           14202       14593     3148740    5  Extended
/dev/hda2               1        7674    61641373+  83  Linux
/dev/hda3            7675       14201    52428127+  83  Linux
/dev/hda5           14202       14593     3148708+  82  Linux swap / Solaris

```

/dev/hda2 holds my filesystem ( / )
/dev/hda3 holds my /home directory

I want to shrink hda2 (I don't need 50 gigs for the root filesystem!!) and add it to hda3.  From reading, the only way to do that is to do a complete backup, reformat and partition, then restore the backup.

So my questions are
   1) Is there a way to shrink /dev/hda2 and add to /dev/hda3 without loosing data and without reformatting?
   2)  If not, what is the best way to go about backing up and restoring my entire system in such a way that I do not have to reinstall ubuntu, reinstall all the additional software I have currently installed, and then set up all the software/config files  (If there is such a way).
   3) Any other ideas/recommendations/comments?

Thanks ahead of time!

---

### Post by laidback on 2007-02-15
Suggest you create a CD of Gparted (from the web), download the ISO file and burn to CD. As it's bootable reboot PC with Gparted CD in drive. Answer a few questions and away you go. Gparted will allow you to reduce partition size and increase it. (provided there's space of course), delete and create as well as move (slide left or right).

You cannot change partitions while they're mounted, but as Gparted is a Live CD you get around that problem. It'll list your hdd's once running.

Search Google for Gparted, it comes up right away.

---

### Post by harty83 on 2007-02-15
GParted is the bomb!  It is definitely going into my tool chest!

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           14202       14593     3148740    5  Extended
/dev/hda2               1        1311    10530576   83  Linux
/dev/hda3            1312       14201   103538925   83  Linux
/dev/hda5           14202       14593     3148708+  82  Linux swap / Solaris

```

Thanks!!!! You saved me a huge amount of time and frustration!

Just out of curiosity, why couldn't qtparted via knoppix do what gparted did?  Qtparted would not allow me to resize the partitions but rather delete/create.

---

### Post by dcstar on 2007-02-15
> **harty83 said:**
> .......
Just out of curiosity, why couldn't qtparted via knoppix do what gparted did?  Qtparted would not allow me to resize the partitions but rather delete/create.

AFAIK qtparted and gparted are just front-ends to the underlying parted program, they should do the same thing.

Booting off a separate disk may be the difference, you cannot manipulate mounted filesystems that you have booted off.

---

### Post by harty83 on 2007-02-15
Knoppix was running from CD and neither partition was mounted.  

If both run from the same underlying program, then knoppix should have been able to do the same thing.  I'll boot up from knoppix again and just play around without actually changing anything to see what was up.

Thanks again!
Alan

---

### Post by laidback on 2007-02-16
harty88

I'm so pleased that you found the idea useful, it is very nice for me to have been of help.

I'll be in need one day too!


Out of interest I've just come across another Live CD which seems to be even better, it's called RIP, I got it off a CD that came with a Linux Format magazine (English mag I'm afraid). It's a small distro with web sites, search for RIP Linux. RIP includes Gparted amongst other goodies, it also has Firefox, so you can surf too, seems very handy at first glance. Another one for the tool box!

laidback

---

