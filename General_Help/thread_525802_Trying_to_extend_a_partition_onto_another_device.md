---
title: "Trying to extend a partition onto another device"
date: 2007-08-14
forum: General Help
---

### Post by Jenga201 on 2007-08-14
I have two 300GB drives on a server with ubuntu server 6.06 installed.

I'd like to expand /dev/sda1 to include another partition /dev/sdb1 so the logical partition is something like 500GB

i'm trying to follow this guide:
[http://fedoranews.org/mediawiki/index.php/Expanding_Linux_Partitions_with_LVM#Adding_a_Logical_Volume](http://fedoranews.org/mediawiki/index.php/Expanding_Linux_Partitions_with_LVM#Adding_a_Logical_Volume)

but i get stuck on this part:
Now that we have everything set up for the merge, let's create the physical volume from home partition
[root@localhost ~]# pvcreate /dev/hda5
  Physical volume "/dev/hda5" successfully created
[root@localhost ~]#

It tells me that it cannot do pvcreate because the /dev/sda1 is mounted.

If i unmount /dev/sda1 from /etc/fstab, linux won't boot...so this doesn't make any sense.

Am i doing this incorrectly?

If anybody has any suggestions on what to do here, it would be really helpful.  Thanks.

---

### Post by bodhi.zazen on 2007-08-14
you will need to do that from a live CD ... That way your root partition will not be mounted.

You realize, I hope, making a LVM is a destructive process (meaning it iwll wipe your existing partition) ?

You could always mount your new hard drive at /media/data or what have you ...

---

### Post by Jenga201 on 2007-08-14
well, the entire reason i want to extend the partition...is because i'd like to just have more space for those files.  right now i'm using it with an ftp server, and it's annoying switching dirs to get other files...not to mention harder to manage it.

---

