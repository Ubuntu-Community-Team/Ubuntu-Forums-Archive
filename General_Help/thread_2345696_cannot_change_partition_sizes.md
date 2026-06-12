---
title: "cannot change partition sizes"
date: 2016-12-07
forum: General Help
---

### Post by Bhakti108 on 2016-12-07
Hi there,

I have just installed 16.04 onto my laptop. I sized the **/** partition to 5gb and my **/home** to the rest of the disk, (minus swap size of course) once I rebooted the new installation a warning came up that I only had minimal space left on **/** 

As I don't yet have anything on **/home**, I loaded gparted and tried to shrink **/home** in order to increase **/**

However Gparted will not allow me to change the size of any partition. I have done this sort of thing before on earlier versions and not sure what is happening and why it will not let me do this. 

Can anyone tell me what to do.

---

### Post by Keith_Helms on 2016-12-07
You'll need to boot from a live CD/DVD in order to change the partition sizes.   You can't change them while they're mounted to a running OS.

---

### Post by yancek on 2016-12-07
> I have just installed 16.04 onto my laptop. I sized the **/** partition to 5gb

I'm surprised it booted at all since, according to the Ubuntu site below, the minimum for a root partition is 8GB.  You should be able to change this from a Live CD/flash drive as suggested.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Bhakti108 on 2016-12-09
Simple really, wasn't thinking straight. Cheers

---

### Post by Bhakti108 on 2016-12-09
ok will resize to 10 gig

---

