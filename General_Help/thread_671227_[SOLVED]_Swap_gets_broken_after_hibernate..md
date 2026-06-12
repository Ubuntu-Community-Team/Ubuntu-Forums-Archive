---
title: "[SOLVED] Swap gets broken after hibernate."
date: 2008-01-18
forum: General Help
---

### Post by Vadi on 2008-01-18
I had my hibernate working fine with 7.10, but after I installed another Ubuntu, and told it to use the same swap space (I was told that would be fine), my swap space gets broken every time I hibernate on my main Ubuntu.

After I set it to hibernate, when it resumes, it boots up normally, not actually resume. It also breaks my swap - gparted says it's "unknown". So I have to format it to be linux-swap and then do sudo swapon -a to use the swap (because I found out painfully that running out of RAM causes Ubuntu to start killing my HD, and it dies itself along with it).

Anyone have any ideas on how to fix swap? Here's my /etc/fstab if it helps any:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d7252cfb-6cb2-4a58-8a1c-7fe8f6657322 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=605b3954-426b-47ad-823a-9481ec7631be /home           ext3    defaults        0       2
# /dev/sda1
/dev/sda1 auto            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0


Thanks!

---

### Post by mcduck on 2008-01-18
I you use Hibernate, you can't share swap between different Linux installs. Hibernate stores the system state into swap partition, and then booting the other OS would overwrite the saved data.

IF you wish to use the hibernate, you'll need to create another swap partition.

---

### Post by Vadi on 2008-01-18
Uh huh. Okay.

So the other Ubuntu is 8.04, which I'm perfectly fine with to reinstall, since I only use that for testing. Could you please outline what should I do?

---

### Post by wawarren on 2008-01-18
I'm in a similar situation, so please share details if you figure out how to repair your partition.  

I used fsck on both of my broken partitions and it fixed one of them, so maybe you can try that.  I'm not very savvy with fixing hardware issues though, so I'm sure you probably already tried that. 

Good Luck

---

### Post by mcduck on 2008-01-19
> **Vadi said:**
> Uh huh. Okay.

So the other Ubuntu is 8.04, which I'm perfectly fine with to reinstall, since I only use that for testing. Could you please outline what should I do?

When reisntalling, just let the installer create another swap partition and set the 8.04 to use that instead of the one you already have.

---

### Post by mcduck on 2008-01-19
> **wawarren said:**
> I'm in a similar situation, so please share details if you figure out how to repair your partition.  

I used fsck on both of my broken partitions and it fixed one of them, so maybe you can try that.  I'm not very savvy with fixing hardware issues though, so I'm sure you probably already tried that. 

Good Luck

You can fix swap with 'sudo mkswap /dev/sda5' (or whatever is the correct partition on your setup.

After that you may need to run 'sudo swapon -a' for the swap to work. Also you need to check that the UUID for the swap partition is correctly set in /etc/fstab. You can use 'blkid'-command to get the correct UUID.

---

### Post by louieb on 2008-01-19
If swap is broken because the UUID chaged you need to update the UUID in two (2) places. (That is if you want to hibernate).
```

/etc/fstab
/etc/initramfs-tools/conf.d

```then run```
sudo dpkg-reconfigure  initramfs-tools
```

Mine broke awhile back  and thats what fixed it.
[Nuts Ubuntu FAQ]("http://louboldt.com/ilinuxmisc.htm")

---

### Post by straki on 2008-03-06
Yes this worked with me too thanks louieb!

---

