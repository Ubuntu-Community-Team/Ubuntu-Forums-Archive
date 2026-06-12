---
title: "Accidentally partitioned a LUKS encrypted drive"
date: 2012-12-08
forum: General Help
---

### Post by trillex on 2012-12-08
I was a major idiot as I was installing a new hard drive and accidentally partitioned /dev/sdb instead of /dev/sdc, which was already partitioned and encrypted with LUKS. 

I'd created a new partition on (apparently spanning the entire drive somehow?) and written the new partition tables before I caught my mistake. Imagine the massive facepalm. 

Funny thing is that, when I go into the Disk Utility, it still shows as encrypted and I can luksOpen the drive just fine, even accepting my password - but when I try to mount it, it tells me that I must specify the filesystem type. Forcing a mount of a ext3 filesystem gives me this:

```

# mount -t ext3 /dev/mapper/drive1 /media/drive1
mount: wrong fs type, bad option, bad superblock on /dev/mapper/drive1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

How the hell do I revert this or how will I save my data, if at all possible?

Funny thing is that Disk Utility seem to show me 2 2 TB partitions on 1 2 TB hard drive. [As seen here.]("http://i.imgur.com/0XZW6.jpg")

---

### Post by TheFu on 2012-12-08
> **trillex said:**
> how will I save my data, if at all possible?

I hope you have a good backup somewhere that you can restore.  Otherwise, it is going to be a very long effort. photorec might be able to help a little, but it is not a trivial effort in my experience.

---

### Post by trillex on 2012-12-08
> **TheFu said:**
> I hope you have a good backup somewhere that you can restore.  Otherwise, it is going to be a very long effort. photorec might be able to help a little, but it is not a trivial effort in my experience.

I can't even "find" the filesystem so I'm thinking of just calling it a sour learning experience and wipe the drive completely.

---

### Post by TheFu on 2012-12-08
When using encryption, it is critical to have excellent backups.  **Absolutely critical.**

---

### Post by alphaamanitin on 2012-12-08
Give TestDisk a try.  I once reformatted my Window's XP NTFS partition to FAT32 with gparted.  After doing a deep scan I was able to restore to the original partition table and format without any lose of data.  It was quite incredible really.  After restoring the boot manager I had my computer back like nothing had happen.  I ended up donating 25 dollars to the guy (I'm a poor grad student or I would have given him much more).  Of course I would strongly advise you to clone your drive and work on the clone so you don't do irreversible damage to the drive while trying to restore.

I have the instructions I used to recover somewhere, I will try and find them and post them within 24 hours.

---

