---
title: "Harvesting the hard drive."
date: 2019-06-15
forum: General Help
---

### Post by Langstracht on 2019-06-15
Booting up my computer has started resulting in GRUB RESCUE and repeated attempts to rectify this have been unsuccessful.

That said it does boot up with a ubuntu 18.04 USB stick.  And it can access the HD, the Disks utility reporting, perhaps surprisingly that the "Disk is OK" but that there are "50 bad sectors".

It shows 4  Partitions:

    Partition 1 (which I think is where the files are): "Ext4" and "Linux (Bootable)" and "mounted"

    Extended Partition 2 

        comprising

    Partition 6 a Linux partition with "Contents unknown" and presumably not mounted.

    and a small Swap partition

So the USB accesses the HD ... but not the files on the drive.

I am hoping that can be rectified but have been unable to do so.

Can anyone help?

Thanks in advance.

---

### Post by Autodave on 2019-06-15
Sounds like the HD is beyond use right now.  Will you be able to get anything off of it?  I doubt it.  About the only thing left to do now is to try reformatting it (which will erase everything on it) and see how many bad sectors it has then.  More than 4 or 5 bad sectors would be cause for replacing it.

---

### Post by TheFu on 2019-06-15
I don't trust Disks.  Use smartctl to see the real SMART numbers. Look at the "raw" column.  If there are any Pending Relocation sectors, then the disk is losing data.  More than 10 relocated sectors and I'm buying a new disk, period.
Most disks have 100+ spare sectors so when 1 fails, the data on it can mostly be relocated and keep working.  

Regardless, I'd be imaging the entire disk (using ddrescue) to a new disk at the first sign of problems. This is in addition to my automatic, daily, backups.  ddrescue doesn't break like dd does if there is a failure. It tries and tries to get the data off, byte for byte.

Exact facts are helpful. Commands and output run in the shell. but I think you have another thread about this disk that's been going for a week. Yes?

---

### Post by Langstracht on 2019-06-15
Thanks for the response.

I'm not familiar with smartctl so I'm not sure if this:

197 Current_Pending_Sector with a RAW_VALUE of 49

is what you mean.

As I have said, I am way beyond "the first sign of problems" which I take it would mean ddrescue isn't an option anymore.  Or is it?

You're correct, I had another thread which was trying to resurrect the computer.  I, not to mention thread contributors have, I think, given up on that and now I trying to turn attention to salvaging the files.

If the HD is accessible (as shown now by both smartctl and "Disks") then should there not be a way to access the files on the HD?

---

### Post by dragonfly41 on 2019-06-15
Suggestions depend on the value of the data to be harvested. Are you willing to gamble on using a recovery app which comes at a cost? Or are you intent on trying opensource recovery tools such as testdisk or photorec?

In a thread some two months back I suggested spinrite ([post #21 here]("https://ubuntuforums.org/showthread.php?t=2415485&page=3&highlight=spinrite")) although I have not used it myself. It has good writeups. At least follow the videoclip to learn more about the innards of disks. The downside is that it only runs in Windows.

I would try testdisk first using a Ubuntu LiveUSB to run testdisk to "harvest" an unmounted failing disk.  Remember that you will need a separate working drive into which any recovered files are saved (you do not save into the drive you are trying to recover).
So ..
LiveUSB with Ubuntu installed with testdisk
Target drive to "harvest"
Another drive into which harvested data is saved.

---

### Post by Langstracht on 2019-06-15
Thanks for responding.

While a "free" solution is always preferable I'd be happy to pay (a modest amount?) to retrieve the files given some reasonable expectation of success.

Tried to use testdisk.  Unsurprisingly it's not part of the 18.04 live USB.  But, surprisingly, "sudo apt install" says it's unable to locate the package.

That option unavailable I'll have a look at spinrite and see if there's some reasonable expectation of it helping.

Thanks again.

---

### Post by dragonfly41 on 2019-06-15
I am on Ubuntu 16.04 and have no experience with testdisk in 18.04.

However I would install GDebi Package Installer and download testdisk.deb to install manually using GDebi.

Here is a 19.04 reference I found ..

[https://www.ubuntuupdates.org/package/core/disco/universe/base/testdisk]("http://I am on Ubuntu 16.04 and have no experience with testdisk in 18.04.However I would install GDebi Package Installer and download https://www.ubuntuupdates.org/package/core/disco/universe/base/testdisk")

[P.S.] I now remember R-Linux as another free option for recovery.

There is a wiki somewhere referring to forensic recovery tools on Ubuntu.

Search "forensic data recovery Ubuntu".

[Here we are.]("https://ubuntuforums.org/showthread.php?t=2370399&highlight=forensic+data+recovery")

---

### Post by TheFu on 2019-06-15
I have spinrite. Think it was $100. For what it is, it is not a bad tool.  It does break a few data recovery NEVER, EVER, rules.  Spinrite tries to modify the broken disk. In data recovery, this is NEVER allowed.  Trying to write to an already broke disk will probably break more sectors or destroy the head.  Use spinrite for bit-rot prevention. Besides that, I don't see much use for it.  Of course, there are thousands of happy customers who swear by it.  If they just  ... 

If you backup and restore your computer(s) from time to time, the entire bit-rot issue is handled.  Heck, backups that read the entire disk force the HDD to access and see which bits are having issues. This allows the HDD to take corrective action before any problems that impact users are seen.

Spinrite doesn't work on HDDs over 2TB in size.  That is really frustrating when you have a full 4TB HDD and it stops at 2TB.

This is bad:
```
197 Current_Pending_Sector with a RAW_VALUE of 49
```
I would clone everything I could using **ddrescue** to a newer HDD ASAP.  I would not have the disk powered for any other purpose than while it is being cloned.  After the cloning finishes, then I'd use that disk for any data recovery efforts.  When cloning, try to use either SATA or eSATA connections, rather than USB.  SATA and eSATA have the full ATA command set, which isn't available to USB storage. For data recovery, it matters.

Once you've tried to recover a system using **testdisk**, you'll decide to have backups from then on.  You'll see why very quickly.  Backups are 1,000,000x easier than getting data using testdisk.

---

### Post by Langstracht on 2019-06-19
Thanks to all for their help but I've decided this is going nowhere and the laptop has been deep sixed.

---

### Post by TheFu on 2019-06-19
> **Langstracht said:**
> Thanks to all for their help but I've decided this is going nowhere and the laptop has been deep sixed.

A bad disk has ZERO to do with the rest of the machine.   $30 gets a new HDD.

---

