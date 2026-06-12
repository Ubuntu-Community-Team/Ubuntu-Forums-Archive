---
title: "Raid array for the desktop"
date: 2017-04-10
forum: General Help
---

### Post by KG4UJD on 2017-04-10
I have built my own machine using: 
I5 6500
16gb ram
2x 1tb wd spinning drives
2x 250gb ssd
128 ssd
gtx 1060


I want to come back to Ubuntu from Windows 10. 
But I can't seem to figure out how to install the system where the two spinning disks are in a mirrored configuration for family pictures and ect. 
And the two ssd's in a striped configuration for steam.

---

### Post by TheFu on 2017-04-11
Hello from just south of you!

RAID solves 2 issues.  High availability and performance.  It never removes the needs for backups, which solve 1,000s of issues. Sometimes to fix RAID issues, the only answer is to restore from backups. For most home users, RAID is the way to write corrupt data, concurrently, to multiple disks, so I always caution people against using it rather than using backups. RAID never replaces the need for solid, restorable, backups. NEVER.

So - assuming you have excellent backups, there are 3 types of RAID which can be used with Linux.
* HW-RAID using a $350 card - usually an LSI brand. Great performance, but HW hassles.
* SW-RAID using mdadmin - the disks are JBOD connected and software handles all the RAID. Slower performance, but very flexible.
* Fake-RAID using motherboard capabilities - HW hassles, not flexible, AND slow performance. Not recommended.

I can't think of any good reason to ever use Fake-RAID.  It has the poor performance of SW-RAID, without the flexibility that SW-RAID provides.  HW-RAID makes sense when performance is the primary consideration in addition to HA, but if you don't have 2 identical RAID cards, beware. Should the RAID card fail, you are likely screwed due to incompatible data storage methods across different RAID card releases. Inside a business, buy 2 RAID cards of exactly the same release, version, model, vendor to protect against this issue.  SW-RAID is extremely flexible.  I've moved SW-RAID across multiple machines, using completely different SATA chips and everything "just worked."

Stopped using RAID5 when large disks became available. Switched to RAID1 when replacing 320G disks with 2TB disks. 

Last fall, one of the arrays had a disk failure and everything kept working. It was a non-event from an availability standpoint. All the running VMs kept going. Removed the failed disk from the array (logically), then removed it physically and swapped in a new 2TB (non-Seagate) disk, added it to the array and let it refill all the data for a few hours. Since I don't have hot-swap array connectors, the VMs were shutdown with the host machine for the physical drive swap, but were running all the other times.  
I've had other failures on the same array over the years, only a few disks failed, but loose SATA connections were an issue early on.  Replaced the included SATA cables with 90 deg connectors years ago and all has been great since.

Ok - enough background.

I've never used RAID on the boot disk or for the OS.  I use it for data volumes only - mainly in support of running VMs.  Just don't need the added complexity for the OS. I don't use RAID for media files or photos. They just aren't worth having 3x the storage (primary, mirror, backups). I can live without media for 5 minutes if the primary fails.  Then I'd just connect the backup disk until the following day when a replacement disk gets put into the box.  This assumes the backups are on the same machine - which isn't usually my situation. Backups happen for OSes on a backup server on the network.  Backups for media happen to specific backup storage on the media server - I'm lazy that way.

TL;DR - How-to for mdadm: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) - appears you can install onto RAID1 disks.

I'm planning to redo our infrastructure here, but will probably drop all RAID use, switching to **sheepdog** for VM storage redundancy.  RAID is so 1990s. Ok, perhaps not, but I can dream. ;)

---

