---
title: "Slow performance - is it my encrypted drive?"
date: 2023-01-31
forum: General Help
---

### Post by uacnt83982803 on 2023-01-31
I am using 22.04 LTS on an Acer Aspire E15, 6GB RAM and Intel Core i3 2.2GHz processor.  The hard drive (spinner) is using LUKS encryption.

The system runs fine, it just seems to be slow.  Looking at the System Monitor, none of the 4 processors are running anywhere near 100% (usually under 25%), and the system isn't using swap (or very rarely).

I'm figuring it's the drive encryption that's making the system respond slowly.  Is that the most likely culprit?

---

### Post by TheFu on 2023-01-31
No.  LUKS with the default settings on any CPU since around 2012 will have AES-ni support. This means that the encryption/decryption is done in hardware and only about 3% overhead, on average.

If you want to know what's slowing things down, you'll want to run some monitoring and watch what is hitting the limits of the system.  Glances is one tool.  Some others are SysUsage, Munin, Cacti, Zabbix.  

There are a few things that can make a system slower than it should be that aren't obvious.
* Really full partitions
* Slow DNS
* Bad wifi situation (if there's lots of interference, the performance can wreak havoc on all networking).  BT speakers and other speakers from quality audio companies have been shown to massively interfere.

Typically, these days the cheapest, fastest, upgrade for a system that improves performance is swapping an old spinning HDD for a new, quality SSD. Even if the system doesn't support NVMe, an SSD connected to the SATA port will be 2-5x faster than the fastest spinning HDDs.  A 500GB SSD from Samsung runs about $60.  That's more than enough for Linux and 99% of stuff we'd have inside a HDD.  Media files (video/music/pictures) can still go on the spinning HDD, if they don't fit inside the SSD.  There are other reasonable consumer SSD SATA vendors, like WD, Crucial, Patriot, just be wary of models that don't have a clear warranty that included TBW endurance numbers.  A few newly popular vendors don't provide TBW endurance numbers.  My data is worth more than that.

Anyway, get some performance monitoring setup and watch it for a few days before deciding anything, though the SSD upgrade from HDD will definitely make a difference for almost every system.

---

### Post by MAFoElffen on 2023-02-01
Not to disagree, but on Virtual Guests (not using real hardware), turning on encryption takes a big performance hit. Having identicle Guest, but with one of the two having encrytion turned on... I don't really notice any changes until it does an update, then on unpacking packages, some packages seem to take forever. Especially if linux-header packages.

---

### Post by TheFu on 2023-02-01
> **MAFoElffen said:**
> Not to disagree, but on Virtual Guests (not using real hardware), turning on encryption takes a big performance hit. Having identicle Guest, but with one of the two having encrytion turned on... I don't really notice any changes until it does an update, then on unpacking packages, some packages seem to take forever. Especially if linux-header packages.

I don't think we're disagreeing.

I've never enabled encryption from inside a VM.  I guess some configurations are obviously just dumb to me.  I have had encryption enabled on the storage where VM files were located, but that's on the real physical hardware.  
So, I wouldn't setup a VM with file-based storage and enable encryption from inside the VM.  Similarly, I wouldn't place a DBMS with lots of transactions inside a VM either.  Is that not intuitively obviously as a bad idea?
I might try setting a a VM on block storage (say an LV) and use encryption for it, but I'd expect it to perform less than on real hardware.  How much less?  A little, not too much, provided the backing storage wasn't slow and was configured with efficient settings for the best possible performance.  If the storage is on NVMe, I doubt I'd notice.  OTOH, it is were on RAID5 spinning disks, perhaps I would notice?

Regardless, I'd use LUKS with default settings, never file-based encryption like encfs or encrytfs.

---

### Post by MAFoElffen on 2023-02-01
This is on VM's with LUKS1, LUKS2, LVM Native encrypted and ZFS Native encrypted... My storage pools for my KVM Guests are on 8TB SATA HDD's. I'm sure it would be faster and less of an impact if it was native on SDD or NVMe, but I am noticing a difference of hours if it updates linux-generic, packages. 

I thought it would help if I added the Host's TPM, but that didn't make any difference at all. 

Note that all those are with encrypted ROOT drives... Not with just DATA drives. I would assume that with just the DATA or home drive encrypted, that there would be no impact.

I was surely surprised at that...

---

### Post by TheFu on 2023-02-01
What if the encryption happens outside the VM?

---

### Post by MAFoElffen on 2023-02-01
If I ever get this Dell Laptop that someone was going to give me for testing, I'll let you know. LOL. Still hasn't happened. I'm still crossing fingers, hoping it does.

---

