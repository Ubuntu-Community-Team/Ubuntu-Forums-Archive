---
title: "Partition shows up as ext4 instantly"
date: 2013-12-18
forum: General Help
---

### Post by mail10 on 2013-12-18
Hi guys,

I just earned a new HDD and cause of some performance optimizations i wanted to create my raid 5 new and clean.

I got two SAMSUNG HD204UI and the new WD20EFRX-68E.

I deleted all the raid stuff on the old discs and created new partitions with gdisk. 
And here is something strange happening on the new WD Red HDD.

Everytime i created a new partition using gdisk (tried parted as well, same here) it shows instantly up as ext4. This only happens on the WD Red, i tried it multiple times.

So whats going on here? I created a partition on all 3 HDDs and the WD is the only one which is showing up here with a never defined filesystem. Here is what blkid says:
```
/dev/sdb1: UUID="396b9def-3509-4e0a-8329-67d36104623f" TYPE="ext4"

```
and parted confirms is:
```
Modell: ATA WDC WD20EFRX-68E (scsi)
Festplatte  /dev/sdb:  2000GB
SektorgrÃ¶Ãe (logisch/physisch): 512B/4096B
Partitionstabelle: gpt


Nummer  Anfang  Ende    GrÃ¶Ãe   Dateisystem  Name              Flags
 1      1049kB  2000GB  2000GB  ext4         Linux RAID  RAID




Modell: ATA SAMSUNG HD204UI (scsi)
Festplatte  /dev/sdc:  2000GB
SektorgrÃ¶Ãe (logisch/physisch): 512B/512B
Partitionstabelle: gpt


Nummer  Anfang  Ende    GrÃ¶Ãe   Dateisystem  Name        Flags
 1      1049kB  2000GB  2000GB               Linux RAID  RAID



```

Any ideas why this is happening?

---

### Post by TheFu on 2013-12-18
The sector sizes are different between the HDDs. Is that safe to be different in a RAID?
Did you mark the WD HDD as RAID in the partition table?

The provided data only shows 2 physical HDDs. RAID5 needs at least 3 physical HDDs, right?

---

### Post by CharlesA on 2013-12-18
> **TheFu said:**
> The sector sizes are different between the HDDs. Is that safe to be different in a RAID?
Did you mark the WD HDD as RAID in the partition table?

The provided data only shows 2 physical HDDs. RAID5 needs at least 3 physical HDDs, right?

I'm guessing they are going to be including sda in the RAID, but it's not listed, so that's just a guess.

But yeah, 3 disks minimum for RAID5, 4 for RAID6.

So far I have not tried to mix drives with different sector sizes.

---

### Post by mail10 on 2013-12-18
I just shortened my output a little bit. And yes the WD one is a 4k but thats not the problem right now.

There is no raid created at the moment so my question is not dependent that there will be one in the feature. 

I just used gdisk to create a partition on each of them and now im wondering why the wd shows me it got a ext4 filesystem.

I do something like this on a Samsung HDD same on the WD HDD
```
micha@homeserver:~$ sudo gdisk /dev/sdbGPT fdisk (gdisk) version 0.8.5


Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present


Creating new GPT entries.


Command (? for help): n
Partition number (1-128, default 1):
First sector (34-3907029134, default = 2048) or {+-}size{KMGTP}:
Last sector (2048-3907029134, default = 3907029134) or {+-}size{KMGTP}:
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): fd00
Changed type of partition to 'Linux RAID'


Command (? for help): w


Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!


Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.

```
After that is done, i get the filesystem marked as ext4 on the partition of the WD HDD and i dont know why.


The WD shows up with ext4:

```

Nummer  Anfang  Ende    GrÃ¶Ãe   Dateisystem  Name        Flags 
1      1049kB  2000GB  2000GB  [COLOR=#ff0000]ext4         [/COLOR]Linux RAID  RAID

```

The Samsung HDD shows up without filesystem which should be correct.
```
Nummer  Anfang  Ende    GrÃ¶Ãe   Dateisystem  Name        Flags
 1      1049kB  2000GB  2000GB               Linux RAID  RAID

```

[B]Note

[/B]I tried to remove the gpt table and create the partition with fdisk using the mbr. Here also ext4 is displayed instantly. I dont understand it...

[B]Fixed it
[/B] 
Dont slap me:
 
I used windows to convert mbr to gpt then created a ntfs partition and moved the hdd back into my linux machine.
I ran "sudo badblocks -vsw /dev/sda" which will overwrite everything so be careful. I actual wanted to check for bad sectors but i canceled it after 10 minutes. 
I createt a new partition with gdisk and now there is no ext4 anymore...

I really dont know what the problem was.

---

