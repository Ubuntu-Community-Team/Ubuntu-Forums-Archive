---
title: "Cannot boot due to failure in filesystem."
date: 2017-09-22
forum: General Help
---

### Post by mrmodern on 2017-09-22
Dear Ubuntu community,

I am putting my best hopes in getting help fixing this problem, all help is appreciated.

[B]The story:

[/B]Few days ago I tried to move some files from one subdirectory to the otherusing Dolphin (KDE). I got an error stating, that there is not enough HDD space left, please note, that I was moving, not copying. I thought, that maybe I need some buffer and at that time my /home partition had only ~600mb left, so I just left it as it is until I remove some junk. However, after a restart, I could not boot any more, just got dropped into root login screen. 

Rebooted into upstart mode. Got a couple of messages that /home partition cannot be mounted, so I skipped, ran smartmonitor and found that indeed there is a failing sector. See attachments for logs. I should note, that when logged in through upstart mode I can access my /home partition, so I was able to backup atleast my most important data into another (NTFS) partition. 

[B]Error from journal and smartmon:

[/B]```
Rgs 22 20:23:36 grapefruit systemd-fsckd[738]: Request to cancel fsck for /dev/mapper/fedora_grapefruit-home from fsckd
Rgs 22 20:23:38 grapefruit kernel: ata1.00: exception Emask 0x0 SAct 0xc0 SErr 0x0 action 0x0
Rgs 22 20:23:38 grapefruit kernel: ata1.00: irq_stat 0x40000008
Rgs 22 20:23:38 grapefruit kernel: ata1.00: failed command: READ FPDMA QUEUED
Rgs 22 20:23:38 grapefruit kernel: ata1.00: cmd 60/00:30:30:3d:21/01:00:56:00:00/40 tag 6 ncq 131072 in
                                            res 51/40:00:30:3d:21/00:01:56:00:00/40 Emask 0x409 (media error) <F>
Rgs 22 20:23:38 grapefruit kernel: ata1.00: status: { DRDY ERR }
Rgs 22 20:23:38 grapefruit kernel: ata1.00: error: { UNC }
Rgs 22 20:23:38 grapefruit kernel: ata1.00: configured for UDMA/133
Rgs 22 20:23:38 grapefruit kernel: sd 0:0:0:0: [sda] tag#6 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Rgs 22 20:23:38 grapefruit kernel: sd 0:0:0:0: [sda] tag#6 Sense Key : Medium Error [current] [descriptor] 
Rgs 22 20:23:38 grapefruit kernel: sd 0:0:0:0: [sda] tag#6 Add. Sense: Unrecovered read error - auto reallocate failed
Rgs 22 20:23:38 grapefruit kernel: sd 0:0:0:0: [sda] tag#6 CDB: Read(10) 28 00 56 21 3d 30 00 01 00 00
Rgs 22 20:23:38 grapefruit kernel: blk_update_request: I/O error, dev sda, sector 1445018928
Rgs 22 20:23:38 grapefruit kernel: ata1: EH complete
Rgs 22 20:23:38 grapefruit systemd-fsck[766]: /dev/mapper/fedora_grapefruit-home: e2fsck canceled.
Rgs 22 20:23:38 grapefruit systemd-fsck[766]: /dev/mapper/fedora_grapefruit-home: ********** WARNING: Filesystem still has errors **********
Rgs 22 20:23:38 grapefruit systemd-fsck[766]: fsck failed with error code 36.
Rgs 22 20:23:38 grapefruit systemd-fsck[766]: Running request emergency.target/start/replace
Rgs 22 20:23:38 grapefruit systemd[1]: systemd-fsck@dev-mapper-fedora_grapefruit\x2dhome.service: Main process exited, code=exited, status=1/FAILURE
Rgs 22 20:23:38 grapefruit systemd[1]: Failed to start File System Check on /dev/mapper/fedora_grapefruit-home.
-- Subject: Unit systemd-fsck@dev-mapper-fedora_grapefruit\x2dhome.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-fsck@dev-mapper-fedora_grapefruit\x2dhome.service has failed.
-- 
-- The result is failed.
Rgs 22 20:23:38 grapefruit systemd[1]: Dependency failed for /home.
-- Subject: Unit home.mount has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit home.mount has failed.
-- 
-- The result is dependency.
Rgs 22 20:23:38 grapefruit systemd[1]: Dependency failed for Local File Systems.
-- Subject: Unit local-fs.target has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit local-fs.target has failed.
-- 
-- The result is dependency.
Rgs 22 20:23:38 grapefruit systemd[1]: Dependency failed for Clean up any mess left by 0dns-up.
-- Subject: Unit dns-clean.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit dns-clean.service has failed.
-- 
-- The result is dependency.
Rgs 22 20:23:38 grapefruit systemd[1]: dns-clean.service: Job dns-clean.service/start failed with result 'dependency'.
Rgs 22 20:23:38 grapefruit systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
Rgs 22 20:23:38 grapefruit systemd[1]: local-fs.target: Triggering OnFailure= dependencies.
Rgs 22 20:23:38 grapefruit systemd[1]: home.mount: Job home.mount/start failed with result 'dependency'.
Rgs 22 20:23:38 grapefruit systemd[1]: systemd-fsck@dev-mapper-fedora_grapefruit\x2dhome.service: Unit entered failed state.
Rgs 22 20:23:38 grapefruit systemd[1]: systemd-fsck@dev-mapper-fedora_grapefruit\x2dhome.service: Failed with result 'exit-code'.
```

```
Error 98 occurred at disk power-on lifetime: 8171 hours (340 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 30 3d 21 06  Error: UNC at LBA = 0x06213d30 = 102841648

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 10 30 3d 21 40 00      03:07:14.792  READ FPDMA QUEUED
  60 08 08 00 3e 21 40 00      03:07:14.792  READ FPDMA QUEUED
  60 08 00 f8 3d 21 40 00      03:07:14.792  READ FPDMA QUEUED
  60 08 f0 f0 3d 21 40 00      03:07:14.792  READ FPDMA QUEUED
  60 08 e8 e8 3d 21 40 00      03:07:14.792  READ FPDMA QUEUED
```
[B]
Any ideas on how to fix this are greatly appreciated. Full logs are attached.

[ATTACH]276809[/ATTACH]
[ATTACH]276812[/ATTACH]
[/B]

---

### Post by SeijiSensei on 2017-09-22
The usual solution is to replace the drive.  Were you looking for some magical alternative?

You could reformat the device with the "bad blocks" switch ("-c") enabled.  This will mark bad sectors as unusable.  For example,

```
sudo fsck -c -t ext4 /dev/sdb1
```

You should be prepared to wait at least a day for this process to complete.

---

### Post by mrmodern on 2017-09-22
Thanks for the answer!
Well, this hard drive is still on warranty. I wasn`t expecting that a single failed block would require replacement... I have heard opinions, that hard failure of a block usually prognoses, that there will be much more failing blocks soon, is it true? 

Side note: I believe I will have a hard time proving warranty service, that the drive needs replacement. And I don`t want to give away my computer for a month...

---

### Post by mrmodern on 2017-09-22
Additional question: Why does SMART test is PASSED if one sector failed so badly?
```
SMART overall-health self-assessment test result: PASSED
```

---

### Post by SeijiSensei on 2017-09-25
I'll go back to my earlier suggestion.  Reformat the device with fsck using the "-c" option to check for bad blocks.

---

### Post by Impavidus on 2017-09-25
> **mrmodern said:**
>  so I was able to backup atleast my most important data into another (NTFS) partition. 


I hope that other partition is on a different hard drive.

---

### Post by mrmodern on 2017-09-26
> **Impavidus said:**
> I hope that other partition is on a different hard drive.
It was the same drive, as there was only one drive in my laptop, but now I successfully got everything transfered to an external drive.

---

### Post by efflandt on 2017-09-26
Can you successfully e2fsck the partition(s) from live/install, or other system booted from external memory or drive? But when I see dev-mapper, I am not familiar with RAID, lvm, or encrypted partitions and how those affect attempting to fix errors.

Drives normally automatically remap good sectors in place of bad sectors. So if you start actually seeing bad sectors, it likely means that all of the sectors reserved for error remapping have been used up. In my case the first sign of that is if I cannot save something to my home directory (no write permission) because Linux automatically remounts it as read-only to prevent further damage.

If you have any Seagate or Maxtor drive on your computer (internal or external) you can get Seatools from seagate.com or similarly if you have any Western Digital drive you can get their diagnostic software from wdc.com which in either case I believe has a version that can boot from CD or USB. Either of those can do a not destructive read test, or if you have gotten everything you need from the drive, can do destructive write/read tests to prove that a drive is defective.

---

### Post by HermanAB on 2017-09-27
Once you have your machine running reliably again, install the fslint utility and deduplicate the file system.  You may be amazed at how much space is saved.  This script will change duplicates into hard links.  Hard links point to one copy of the file and when you delete hard links, the file will only be removed once the last link is deleted (IMHO soft links are evil and should never be used!).

Here is a little script I made to launch findup on my Fedora machine.  Ubuntu may be a little different:

#! /bin/bash
# Use the script findup, part of fslint package
# to convert duplicate files into hard links.
sh /usr/share/fslint/fslint/findup -m /home/herman/Data

This may take a looong tiiiime...
;)

---

### Post by mrmodern on 2017-10-16
Thank you all for suggestions. I loaded live usb and ran e2fsck on "/" partition. It found many errors, yet managed to fix everything. After that I was able to successfully boot into my system. After that, I downloaded WD diagnostic software and checked my HDD, it found no errors and smart log still says that there is no bad sectors and no bad sectors were ever reallocated. It remains a mystery to me, at first it looked as if the drive is dead/dying, but now it works perfectly, this thread should be closed I believe, but maybe someone still has thoughts about what was the reason this unpleasant thing happened?

---

