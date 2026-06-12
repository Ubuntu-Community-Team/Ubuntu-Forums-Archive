---
title: "MDADM raid5 recovery help!"
date: 2015-06-25
forum: General Help
---

### Post by jason_martin on 2015-06-25
Not sure if this is the right area to post but I'm freaking out a little bit and need to get this posted asap.


So I had a mdadm raid5 consisting of 4 3TB drives with 1 disk redundancy. 1 drive failed so I ordered and installed a new drive. Well being the idiot I am, when starting to prep the new drive to add back into the raid I selected the WRONG drive. During the reboot after installing the new drive I guess the SDx letters changed so when I used fdisk to delete any partitions on what I thought was the new drive I actually deleted the partition on one of the 3 remaining drives!! Now I've got no data. This raid consisted of ALL of my person docs, movies, pictures, etc so I REALLY need them back. 


Can I rebuild the partition on the drive I messed up and get the data back? I haven't done anything to the drive so nothing has been written to it since I rebooted. Please help! I am just now getting into linux software raid so I am not real sure what to do.

---

### Post by howefield on 2015-06-25
> **jason_martin said:**
> Not sure if this is the right area to post but I'm freaking out a little bit and need to get this posted asap.

Thread moved.

No, it wasn't the best area, unless all you wanted to do was chat about your problem, let's try here.

Good Luck.

---

### Post by jason_martin on 2015-06-25
Thank you

---

