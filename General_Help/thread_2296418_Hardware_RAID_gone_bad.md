---
title: "Hardware RAID gone bad?"
date: 2015-09-25
forum: General Help
---

### Post by thezman007 on 2015-09-25
Let me try to start at the beginning and include as many details as possible:

PSU: Corsair TX650
MOBO: Gigabyte 990FXA-UD3 Rev. 1
CPU: AMD FX 6200 3.8Ghz six core
RAM: 2x4GB Patriot Series and 2x4GB G.Skill Ripjaw (16GB total)


I set up a RAID1 between 2 WD500GB drives with my BIOS settings when I built this computer a couple years ago. I ran Ubuntu 12.04, 12.10, 13.04, and 13.10 progressively without any real problems except for the inevitable driver issues and/or self-created problems. I needed to upgrade to an LTS version, particularly one that didn't have a memory leak, and did so to 14.04.2 LTS from a USB without incident. I encrypted my drive at this time as I always have for the past few years whenever installing a Linux system. I installed from scratch and downloaded all my necessary files from my cloud backup. I run a Win7 VM with Virtualbox daily for Quickbooks for my business. (Man I *wish* QB would go native to Linux!!!)

A few months ago(?) my system started to shutdown without warning maybe once every couple of days. At some point in time I remember seeing that one of my BIOS chips was corrupted! Thankfully this mobo has DualBios for just such a problem which I believe means that it overwrote the corrupt BIOS with the good copy, but don't quote me on that :) I have not received any other corruption messages since. At roughly the same time it took 2 "boot ups" to get Linux to start. It would boot one time just fine. The next time it would POST, show the BIOS screen, pass the RAID controller screen and say "Loading Operating System..." in the upper left hand corner and the screen would go purple for a few seconds then the monitor would go into power saving mode. A push of the reset button would solve it, but regardless of anything else trying to boot to the HDD and not a CD or USB always resulted in an every other time result. 

So I RMA'd my PSU and received their replacement in the mail to use while the "defective" one was repaired/replaced. Upon changing over the PSU to the new one, I noticed within the day that it acted the same way. After a few more days I had confirmed that the new PSU made zero difference and sent it back (thanks Corsair :p )

A memtest run gave me 3 passes on all sticks without errors. I also checked 2 sticks individually for 11 and 13 passes as well. I didn't check the other 2 individually because I felt pretty certain they were good. 

I then tested my HDDs with native Linux utilities as well as a SeaTools FREEDOS. All SMART short and long test passed with flying colors.

That leaves the motherboard right? So I moved ALL my stuff over to another motherboard: CPU, PSU, RAM, etc. And then my problem...persisted. :icon_frown: It still took 2 boots to get into Linux which then checks my disk for erros, and it died last night while I was blissfully sleeping like a warrior who had vanquished his foe. After playing with the LAN driver to get the internet to work, I come to you, hat in hand, wondering if anyone can help with this challenge. 

*I* believe it to be a problem with the RAID partitions that Linux occasionally just doesn't like. Gparted spits out errors whenever I try to open it, errors like this:
```
======================
libparted : 2.3
======================

(gpartedbin:5434): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 6 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 26 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 25 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 51 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 50 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 65 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 64 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 89 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 88 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 92 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 91 was not found when attempting to remove it
Could not stat device /dev/mapper//dev/sda: "sil" and "pdc" formats discovered (using pdc)! - No such file or directory.
Could not stat device /dev/mapper//dev/sda: "sil" and "pdc" formats discovered (using pdc)! - No such file or directory.
Could not stat device /dev/mapper//dev/sda: "sil" and "pdc" formats discovered (using pdc)! - No such file or directory.
Could not stat device /dev/mapper//dev/sda: "sil" and "pdc" formats discovered (using pdc)! - No such file or directory.
Could not stat device /dev/mapper//dev/sda: "sil" and "pdc" formats discovered (using pdc)! - No such file or directory.

(gpartedbin:5434): GLib-CRITICAL **: Source ID 747 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 746 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 754 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 753 was not found when attempting to remove it
Device /dev/mapper/pdc_eefiebjcc2 not found
device-mapper: table ioctl on  failed: No such device or address
Device /dev/mapper/pdc_eefiebjcc2 not found
device-mapper: table ioctl on  failed: No such device or address
device-mapper: create ioctl on pdc_eefiebjcc2 failed: Device or resource busy
Failed to add partition 2 (No such device or address)

(gpartedbin:5434): GLib-CRITICAL **: Source ID 910 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 909 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 915 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 914 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 918 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 917 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 921 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 920 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 926 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 925 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 929 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 928 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 1502 was not found when attempting to remove it

(gpartedbin:5434): GLib-CRITICAL **: Source ID 1507 was not found when attempting to remove it

```

Do you agree with me? Do you also believe that RAID may have been invented by Loki the trickster god? Can anyone offer advice on how to rectify this partition situation? 

Worst case, can I format one of the drives and copy the information I need over to the new drive WITHOUT retaining the RAID status/issues?

---

### Post by TheFu on 2015-09-25
That's a bunch of back story that probably isn't need.  Short version.
* using fakeRAID
* swapped systems (Identical MBs)
* seeing partition errors and having boot issues 50% of the time
Is there a fix?

My reply:
RAID on the motherboard is almost always "FakeRAID" and has all the liabilities of fast HW-RAID (HW bound) with none of the flexibility of SW-RAID, yet that is the performance for FakeRAID.

If you need disk performance, a quality HW-RAID card from LSI is what you need.

If you don't need high disk performance, Linux SW-RAID is what you want - assuming you actually need RAID at all.

I honestly cannot think of an good reason to use FakeRAID.  It isn't just me with this idea:
[https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid](https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid)

RAID is for HA - nothing else and doesn't remove the need for backups, but if you are doing encryption, you already know the importance of backups.

I googled for known fakeRAID issues with that MB - seems there are some with v1.1, v2 and v4 versions. Are both your MBs the exact same?

---

### Post by thezman007 on 2015-09-25
> **TheFu said:**
> That's a bunch of back story that probably isn't need.  Short version.
* using fakeRAID
* swapped systems (Identical MBs)
* seeing partition errors and having boot issues 50% of the time
Is there a fix?

My reply:
RAID on the motherboard is almost always "FakeRAID" and has all the liabilities of fast HW-RAID (HW bound) with none of the flexibility of SW-RAID, yet that is the performance for FakeRAID.

If you need disk performance, a quality HW-RAID card from LSI is what you need.

If you don't need high disk performance, Linux SW-RAID is what you want - assuming you actually need RAID at all.

I honestly cannot think of an good reason to use FakeRAID.  It isn't just me with this idea:
[https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid](https://superuser.com/questions/245928/does-fake-raid-offer-any-advantage-over-software-raid)

RAID is for HA - nothing else and doesn't remove the need for backups, but if you are doing encryption, you already know the importance of backups.

I googled for known fakeRAID issues with that MB - seems there are some with v1.1, v2 and v4 versions. Are both your MBs the exact same?

Yeah probably not needed, but I hate when things get left out and fixes don't take into account things the helper wasn't aware of that might affect how effective the solutions are.

"Raid is for HA - nothing else" What HA are you talking about? Hardware Acceleration?

Also, no the new motherboard is a different model/brand entirely, hence the difficulty with the LAN drivers.

As for the fakeRAID issues with the original mobo, It's rev 1, not 1.1, 2, or 4 so I don't see how that applies. Maybe I don't need RAID as the times my drives died were pre S.M.A.R.T. systems I think. 

The main question is can these partitions be fixed to stop my boot/dying issues if that is in fact the problem? My swap partition also doesn't seem to load properly so maybe it's filling up and then it messes up the system? 16GB is kind of a lot to fill up though.

---

### Post by TheFu on 2015-09-25
HA = High Availability.  Surviving a failure to keep a system running.
[https://en.wikipedia.org/wiki/High_availability](https://en.wikipedia.org/wiki/High_availability)

If the MB models are different, I'm surprised that the RAID disks are readable at all in a new system. HW-RAID and fakeRAID are tied to the HW used.  SW-RAID is not. 
[http://skrypuch.com/raid/](http://skrypuch.com/raid/) I think moving the disks to a new MB probably corrupted the data.

16G of swap?  Does the workload really need that?  I'd be surprised if a home system used more than 4G of swap - unless you are doing something strange.  What do the log files show? Always start with the logs.

Rev 1 ... there is a reason they have made later revisions. Something wasn't right in the original or new features required new chips. Usually both. The revs are related.

---

### Post by tgalati4 on 2015-09-25
Can you boot successfully in a degraded state?  If so, start copying your important files--make a backup.  Create a new 14.04 LTS system and skip RAID1, use simple ext4.  Your new swap file only needs to be slightly larger than RAM if you want to hibernate--that is why you have a 16 GB swap file.  If you don't care about hibernation--copying the entire RAM to hard disk then shutting down power--then make your swap 4 or 8 GB.

With your fakeRAID, can you pull out one drive completely and boot?  If so, now is the time to backup and create a new system without RAID--less headaches and no real benefit.

---

