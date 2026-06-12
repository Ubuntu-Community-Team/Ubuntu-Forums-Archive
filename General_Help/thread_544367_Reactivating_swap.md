---
title: "Reactivating swap"
date: 2007-09-06
forum: General Help
---

### Post by mr bob on 2007-09-06
I have been trying to get hibernate to work on feisty and discovered that my swap was deactivated.

Every time I attempted to reactivate swap with swapon -a I get this:

```

swapon: cannot stat /dev/disk/by-uuid/a7759246-213b-436f-88ad-730cb98929d9: No such file or directory

```

This is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=afc6d649-a6fa-402b-9a89-cef5f0abc8a9 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=a7759246-213b-436f-88ad-730cb98929d9 none            swap    sw            
  0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Can anybody help? Thanks

mr bob

---

### Post by logos34 on 2007-09-06
what does

**ls -l /dev/disk/by-uuid**

show?

---

### Post by mr bob on 2007-09-06
> **logos34 said:**
> what does

**ls -l /dev/disk/by-uuid**

show?

total 0
lrwxrwxrwx 1 root root 10 2007-09-06 14:55 1618-1700 -> ../../hdb1
lrwxrwxrwx 1 root root 10 2007-09-06 14:55 640c5ebe-6983-45be-9b0c-b4d5fc07ace2 -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-09-06 14:55 afc6d649-a6fa-402b-9a89-cef5f0abc8a9 -> ../../hda1

Aha, yes that looks different. Thanks for the reply.

Is that because I reinstalled a partition with partimage and it may of been from a different install?

What can I do to fix it?

---

### Post by logos34 on 2007-09-06
The uuid changes whenever you (re)format a partition, even if the size remains the same and you're just reinstalling over it.

Just take out the uuid:
[B]
/dev/hda5 none swap sw 0 0[/B]

try that

---

### Post by notwen on 2007-09-06
This is a tad off-topic, but are there any advantages of using the /dev/partition# format over the UUID?  I had to do this myself a couple of weeks back, when modifying my partition table and growing a partition.

---

### Post by Steve1961 on 2007-09-06
> **notwen said:**
> This is a tad off-topic, but are there any advantages of using the /dev/partition# format over the UUID?  I had to do this myself a couple of weeks back, when modifying my partition table and growing a partition.

My understanding is that the UUID is persistent, even if the partition name changes.  Since kernel 2.6.19 (I think?) some changes affected the way that devices were named.  According to the arch wiki:

> If you have more than one sata/scsi or ide disk controller, the order in which they are added is random. This may result in device names like hdX and hdY switching around randomly on each boot. The same goes for sdX and sdY. Persistent naming allows you not to worry about this at all. 


see:

[http://wiki.archlinux.org/index.php/Persistent_block_device_naming](http://wiki.archlinux.org/index.php/Persistent_block_device_naming)

---

### Post by mr bob on 2007-09-06
> **logos34 said:**
> The uuid changes whenever you (re)format a partition, even if the size remains the same and you're just reinstalling over it.

Just take out the uuid:
[B]
/dev/hda5 none swap sw 0 0[/B]

try that

Yep that did the trick, great thanks.

I'm sure my /etc/fstab was like that anyway, don't remember when the UUID stuff got in there!

---

### Post by logos34 on 2007-09-06
> If you have more than one sata/scsi or ide disk controller, the order in which they are added is random. This may result in device names like hdX and hdY switching around randomly on each boot. The same goes for sdX and sdY. Persistent naming allows you not to worry about this at all.

That's one advantage I had forgotten about, to be honest...A lot of people have newer boards with two different sata controllers, so I guess in that case it might make sense.  Some guy had that problem in these forums not to long ago--two contollers and musical sata drive names on every boot.   But for your average user with static internal hard disks and hotpluggable external drives that the system automounts every time, I just don't see the need.  I was just going on about this in another thread.  These uuids can be a pain in the a--.  I took out the uuids for my swap and other non-root ext3 partitions because I'm always installing some new distro or flavor of ubuntu, and I just got tired of changing the damn things so they mount when I boot my main install.  They're all ext3 so it was a no brainer.

---

### Post by logos34 on 2007-09-06
> **mr bob said:**
> Yep that did the trick, great thanks.

I'm sure my /etc/fstab was like that anyway, don't remember when the UUID stuff got in there!

Ubuntu switched to uuids starting with Edgy 6.10...if you upgraded from dapper to edgy then that would be one possible explanation.

---

### Post by mr bob on 2007-09-06
> **logos34 said:**
> Ubuntu switched to uuids starting with Edgy 6.10...if you upgraded from dapper to edgy then that would be one possible explanation.

It's strange, I've been using Feisty since it was released.

---

