---
title: "Increase the size of Ubuntu using GParted"
date: 2015-08-28
forum: General Help
---

### Post by Viktorija on 2015-08-28
Hello,

I have no idea what to do... I tried to increase my size using GParted from 8 to 20 gb and now that's my final view:
[http://i57.tinypic.com/i2rqir.png](http://i57.tinypic.com/i2rqir.png)
Seems fine but when I checked, it shows me the same old size... :( :(
[http://i60.tinypic.com/2hz3f2f.png](http://i60.tinypic.com/2hz3f2f.png)

---

### Post by Bucky Ball on 2015-08-28
*Thread moved to **General Help**.*

Welcome. Could have something to do with the fact it is an LVM partition. Encrypted I believe. Don't know anything about them but I have bumped your thread. Good luck. :)

---

### Post by yancek on 2015-08-28
I'm not sure GParted can resize lvm partitions.  I don't see anything obvious at the GParted Manual link, second link below.  Are you doing this from a Live DVD/flash drive as it won't work from the installed system.  You could try doing an online search to find sites such as the one below for help while you are waiting for someone else to respond.

[http://www.tecmint.com/extend-and-reduce-lvms-in-linux/](http://www.tecmint.com/extend-and-reduce-lvms-in-linux/)

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

### Post by sandyd on 2015-08-28
> **Viktorija said:**
> Hello,

I have no idea what to do... I tried to increase my size using GParted from 8 to 20 gb and now that's my final view:
[http://i57.tinypic.com/i2rqir.png](http://i57.tinypic.com/i2rqir.png)
Seems fine but when I checked, it shows me the same old size... :( :(
[http://i60.tinypic.com/2hz3f2f.png](http://i60.tinypic.com/2hz3f2f.png)

A bit of explanation:
When you use LVM, the partition that you see in df is _not_ a partition. In LVM, it is called a LV (Logical Volume). The Logical Volume is "categorized" in what is called the Volume Group, which is a way of categorizing Logical Volumes. Meanwhile, Logical Volumes reside on the LVM PV (Physical Volume), which is the partition you see in GParted.

As a result, when you resize the partition in GParted, it does nothing but increase the size of the LVM PV.

If your using ext4, (can be found if you run mount -l), continue with the below, if not, post the output of mount -l. Please ensure that backups have been created before running.
```

sudo pvresize /dev/sda5
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-root
sudo resize2fs /dev/mapper/ubuntu--vg-root
sudo e2fsck /dev/mapper/ubuntu--vg-root

```

---

