---
title: "Windows Fails to boot after running Ubuntu from live USB"
date: 2016-08-25
forum: General Help
---

### Post by willdabeast2 on 2016-08-25
After booting from a live USB of Ubuntu, I saw that my SSD that had Windows installed was in use, so I attempted to remove the Linux partition, sine I wanted all files to be managed on the flash drive only, but instead, I may have removed everything on my hard drive. I'm still not entirely sure what I did. Now, when I remove the flash drive, grub launches in rescue mode. Nothing works unless I reinsert the flash drive and boot from Ubuntu. I tried using grub to launch from the drive (hd0,msdos5), but to no avail. I booted from Ubuntu, installed Boot-Repair, and the o my option it gave me was to run a scan and ask for help with this link. Could anyone help me out, please? I'm starting to think I may need to purchase a new copy of Windows.
[http://paste2.org/PW5y0sFb](http://paste2.org/PW5y0sFb)
Thank you so much for your time!
-Will

EDIT: Here's a picture of the disks application after I messed with it. Should it be labeling my once near-full hard drive as "Free Space", even if I filled it using Windows?
http://imgur.com/oPzSjuF

---

### Post by oldfred on 2016-08-25
You have to make sure Windows fast start or always on hibernation is off. 

Both report & screenshot only show extended partition and swap.

You may be able to use testdisk to restore missing partitions.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by willdabeast2 on 2016-08-25
Thank you so much! I'm at school right now, but when I get home, I will try this. Thanks again!

---

