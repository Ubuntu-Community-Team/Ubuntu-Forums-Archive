---
title: "Help with Ubuntu 22.04 server with Fake Raid not mounting"
date: 2022-11-09
forum: General Help
---

### Post by silverspr on 2022-11-09
Hello I've done a clean install of Ubuntu 22.04 server but the fake raid (NVidia) will **not mount**. This raid setup has worked since 16.04. I disconnected the hard drives in the raid set before installing the server.  Once the server was installed and rebooted, I installed dmraid (wasn't included with iso ??). Then connected the raid drives to the system and rebooted.  The raid (mirror) is activated but there seems to be a problem with the partition raid flag on /dev/mapper/nvidia_xxx.  From gparted, if I deselect and reselect the raid flag the drive error is fixed. The raid drive then mounts. But this fix is lost each time there is a reboot.  

I also tried removing the metadata from the raid sets, this just served to break the raid and I wasn't clear on how to use the dmraid format function to recreate the raid.  Then I broke the raid at the hardware level (in bios), rebooted, recreated the array at the hardware level and rebooted.  The /dev/mapper_xx was recreated but had the same partition error as described above.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291241&stc=1[/IMG]

Does anyone have any ideas? I've been working on this for a few days!  My next step would be to either disassemble the fake raid and use mdadm or try go back to 20.4.5 ... But would really like to try fix the issue for better understanding of what is happening.
thanks for your help 
-D

---

### Post by TheFu on 2022-11-11
IDK, but wasn't dmraid deprecated in 2020 for the fake-raid built into mdraid?
If you aren't dual booting with multiple OSes, there's no good reason to use fake-raid. Use SW-RAID, either from mdraid or LVM or ZFS.

FakeRAID has all the problems of HW-RAID being tied to exact motherboard chips, with none of the performance and flexibility that SW-RAID provides.  I'm a software RAID setup from around 2008 that has been moved forward between 3 different computers all this time. It isn't for the OS, it is strictly for data, but works well, survived a few dead disks over the decades.  The RAID enclosure was originally SW-RAID5 (4x320GB) with smaller disks. Around 2012, moved to 4x2TB disk in RAID1. Had 2 Seagate 2TB drives die exactly when the warranty on each expired, replace them with non-Seagate HDDS (WD and Toshiba)

I know the LVM RAID1 works for the OS. Set it up less than 2 months ago on a system here. With SSD reliability, we stopped using RAID on SSDs and only use it for spinning disk storage and only after our backups are 100% good first.

---

### Post by silverspr on 2022-11-12
Thanks for your thoughts, looks like I'm moving to mdadm.  Will I be able to assemble the raid array from dmraid in mdadm.  I've tried but of course there is no config file so its not aware of any arrays.  But was hoping you might know how to do this, rebuild a dmraid using mdadm.  Otherwise, I guess I go the create route and restore from backups.

---

### Post by TheFu on 2022-11-13
> **silverspr said:**
> Thanks for your thoughts, looks like I'm moving to mdadm.  Will I be able to assemble the raid array from dmraid in mdadm.  I've tried but of course there is no config file so its not aware of any arrays.  But was hoping you might know how to do this, rebuild a dmraid using mdadm.  Otherwise, I guess I go the create route and restore from backups.


I assume you have already seen these: 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) - really old 10.04-ish
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://manpages.ubuntu.com/manpages/focal/en/man7/lvmraid.7.html](https://manpages.ubuntu.com/manpages/focal/en/man7/lvmraid.7.html)

I thought that every major RAID method used slightly different encoding.  With HW-RAID, even a slight change in the HBA revision can break access to data, which is why enterprises always purchase spare HBAs when they go with HW-RAID.
The same usually applies to FakeRAID.  It is tied to the specific hardware.  So, the FakeRAID that is part of mdadm needs to work exactly like the FakeRAID from dmraid for access to be possible.  That's my guess.

Now, SW-RAID is all about fast SATA/SAS connections and doesn't depend on any HW.  The SW-RAID I've used has migrated between completely different SATA controllers without any issues, so, I would encourage you to drop any ties to FakeRAID/HW ASAP and move to pure SW-RAID. If that means creating new SW-RAID array(s), then do that.

Additionally, if this is for data only, I'd strongly push to using ZFS for a number of reasons, which you can research.
If this is for the OS, then I'd push for using LVM2+RAID.  There's no need for the added layer of mdadm and if it storage is important enough for RAID, then it is important enough for an enterprise volume manager like LVM or ZFS.

But only you can decide and regardless, before making any long term choice, it would be smart to practice using whatever you think will be used within a virtual machine, check the RAID failure modes, RAID recovery steps, and see how each behaves. Better to be surprised with unimportant testing, before important data is used, right?

---

### Post by silverspr on 2022-11-14
Thanks again for your insight.  ZFS is intriguing and I'm very interested.  I've set up a basic mirror but have difficulty understanding how to mount the pool....not a quick fix.  I'm off to do more searching.  Again thanks.

---

