---
title: "Very Odd Fdisk Output"
date: 2008-02-12
forum: General Help
---

### Post by Schroedinger on 2008-02-12
My Current machine has 3 500GB drives in it. My / drive has on it a 300GB NTFS partition which is showing up nicely. My other two drives are each EXT3 formatted drives and Ubuntu is mounting and using them brilliantly.

Which is where my problem comes in. Both FDISK and Gparted say my two 500 GB drives that aren't / have no partitions or partition table, but Ubuntu mounts them fantastically. This is proving to be a problem because I want to access the data in them on the windows partition as well, but it is becoming increasingly frustrating!

The quirk is that the two 500GB drives were removed from the Machine when I reinstalled ubuntu, I then put in the two drives, mounted them and chowned and chmodded the contents. Both are almost full with media and assorted backups and thus I don't want to lose the data.

How can I repair the partition tables on the two and have Gparted and Fdisk notice the partitions on the disk so I can access them in windows?

Attached Images for proof

Fdisk output
[[IMG]http://img142.imageshack.us/img142/7138/fdiskoutputmo0.png[/IMG]](http://imageshack.us)

/etc/fstab contents
[[IMG]http://img179.imageshack.us/img179/1350/fstabscreenshotfv7.png[/IMG]](http://imageshack.us)

/media Nautilus view
[img]http://img529.imageshack.us/img529/3104/mediafolderwe7.png[/img]

Any help would be absolutely welcome, I'm totally scratching my head here.

---

### Post by deepclutch on 2008-02-12
for sure,your mount points will all fails,if u do below thing:still it fixes partition order.
```
sudo fdisk /dev/sda
```
press "x",then "f",then "w".
now do a "sudo partprobe"

-do the same with /dev/sdb /dev/sdc disks. :D

you can do a fsck.ext3 -fvy  partnno to ur **unmounted** partitions in other hdds

---

### Post by Schroedinger on 2008-02-12
> **deepclutch said:**
> for sure,your mount points will all fails,if u do below thing:still it fixes partition order.
```
sudo fdisk /dev/sda
```
press "x",then "f",then "w".
now do a "sudo partprobe"

-do the same with /dev/sdb /dev/sdc disks. :D

you can do a fsck.ext3 -fvy  partnno to ur **unmounted** partitions in other hdds

They mount fine in Ubuntu, they mount and work great, it's just that Gparted and Fdisk don't see the partitions in the two 500GB disks. I'm not going to rewrite the partition tables if I'm going to lose the content on the disks...

EDIT: doing the x then the f for sda and sdb says no work to be done, as does sdc, all say partition order is correct.

Which means I've stumbled on a bigger problem

---

### Post by Schroedinger on 2008-02-12
> **deepclutch said:**
> for sure,your mount points will all fails,if u do below thing:still it fixes partition order.
```
sudo fdisk /dev/sda
```
press "x",then "f",then "w".
now do a "sudo partprobe"

-do the same with /dev/sdb /dev/sdc disks. :D

you can do a fsck.ext3 -fvy  partnno to ur **unmounted** partitions in other hdds

Yeah dude that caused my machine to no longer mount one of my drives, causing me to lose like 500GB of data that I'm currently trying to recover.

Two questions: best way to recover my data? (At the moment I'm using testdisk)

Second: What do I do to fix the partition issues?

---

### Post by Herman on 2008-02-12
TestDisk should be the best way to recover your data and fix your partition table at the same time, in case you haven't used TestDisk before, here's a webpage with some illustration to give you an idea what it's like, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").
Regards, Herman :)

---

