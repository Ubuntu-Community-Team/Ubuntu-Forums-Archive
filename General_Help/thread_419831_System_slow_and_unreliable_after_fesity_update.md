---
title: "System slow and unreliable after fesity update"
date: 2007-04-23
forum: General Help
---

### Post by szim90 on 2007-04-23
Hello.

After upgrading to fesity from edgy, I noticed two new problems developed:

First, the system sometimes stalls after the gdm login screen. After entering my name and password, the system switches to the logging-in background color but the ubuntu/gnome splash screen does not appears. I still can get access to the virtual terminals and from there I can reboot the system and try again, but I did not have this problem in Edgy.

Second, the system runs considerably slower. I noticed that all of the movie players (mplayer, vlc, xine, totem) lock up after a few minutes. If I fast forward or rewind within the file, the program locks up almost immediately afterwards. I have tried using different files that I know played correctly when I was using Edgy, but it still locks up (mplayer still responded to a quit, xine needed a kill -9). 


The only things that I did after I upgraded from dapper to edgy was I removed mdadm from the system (I didn't have a raid and never configured mdadm - I installed it because I though I was going to install a raid, but never did). I also adjusted the xorg.conf so it had the same refresh rate as it did in Edgy (somehow it got changed to a lower rate). I don't know if either of these things is related to the problems.

Does anyone know some way to fix this? I am running Feisty on a PowerMac G4 (Quicksilver model).

Thank you for any help,
szim90

---

### Post by shof2k on 2007-04-23
I have a similar problem.  The gnome desktop appears to stutter with the cursor jumping from point to point.  Using system monitor shows nothing taking up CPU, but the machine still feels like treacle.

I'll try a kernel recompile in the next couple of weeks.

---

### Post by saxenaks on 2007-04-24
I am also facing similar. 7.04 is making my system too slow to use.

I noticed this error in syslog

Apr 24 12:02:57 localhost kernel: [ 4675.516000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 24 12:02:57 localhost kernel: [ 4675.516000] ata1.00: cmd ca/00:08:cf:e7:26/00:00:00:00:00/e2 tag 0 cdb 0x1e data 4096 out
Apr 24 12:02:57 localhost kernel: [ 4675.516000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)

This error is logged again and again. The system stall and then I notice this error in syslog.

Also there is another post which also tells about system running slow [http://ubuntuforums.org/showthread.php?t=420350](http://ubuntuforums.org/showthread.php?t=420350)

---

### Post by saxenaks on 2007-04-24
The complete log is:

Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1.00: cmd ca/00:08:f7:50:36/00:00:00:00:00/e0 tag 0 cdb 0x1e data 4096 out
Apr 24 12:13:53 localhost kernel: [ 5331.000000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr 24 12:13:53 localhost kernel: [ 5331.000000] ata1: soft resetting port
Apr 24 12:13:53 localhost kernel: [ 5331.384000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 24 12:13:53 localhost kernel: [ 5331.496000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 24 12:13:53 localhost kernel: [ 5331.496000] ata1.00: configured for UDMA/33
Apr 24 12:13:54 localhost kernel: [ 5331.688000] ata1.01: configured for UDMA/33
Apr 24 12:13:54 localhost kernel: [ 5331.688000] ata1: EH complete
Apr 24 12:13:54 localhost kernel: [ 5331.712000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr 24 12:13:54 localhost kernel: [ 5331.724000] sda: Write Protect is off
Apr 24 12:13:54 localhost kernel: [ 5331.724000] sda: Mode Sense: 00 3a 00 00
Apr 24 12:13:54 localhost kernel: [ 5331.744000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 12:13:54 localhost kernel: [ 5331.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Apr 24 12:13:54 localhost kernel: [ 5331.776000] sda: Write Protect is off
Apr 24 12:13:54 localhost kernel: [ 5331.776000] sda: Mode Sense: 00 3a 00 00
Apr 24 12:13:54 localhost kernel: [ 5331.776000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by saxenaks on 2007-04-24
After three hours system is running fine. I am not sure what fixed the problem. However this will happen again when I restart the system.

---

### Post by saxenaks on 2007-04-24
There is a bug for this issue [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

It is strange that this bug was filed on Feb 11, 2007 and not fixed will date. Moreover a upgrade is made public with this bug.

---

### Post by shof2k on 2007-04-29
I looked at [bug 84603]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603"), but it doesn't apply to me as I don't have any removable media present and my harddrive is IDE connected.

[Bug 88815]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/88815") mentions some xorg libraries.  I downgraded the modules as advised, but the problem is still there. Tried using iceWM, but get the same problem which rules out metacity.  

Amazingly it is intermittant, sometimes starting on boot, other times taking an hour to cause problems. This makes me think it is some sort of contention of resources.  I have a feeling the problem is with xorg, gnome, or directly with the kernel.

I'm going to install KDE to rule out gnome.  Is there anyone who can provide a manual on how to get good diagnostics and logs from xorg and the kernel?  I'm reluctant to use launchpad until I can provide some detailed information on this.

I'll manage my production partition on Edgy for now, but I'd like to sort this out sooner rather than later

---

### Post by shof2k on 2007-04-29
Loaded KDE and still have the same problem, so it's either a system wide problem, damn!

Specs involved.
I-friend nc202i4 laptop
Celeron PIV 2.0Ghz
512MB RAM
Intel 845G graphics

---

### Post by jrock2004 on 2007-05-01
When locking up does your window go dark? That is what is happing to mine.

I am wondering if it is a certain app? I am going to reinstall and see what happens 1 by 1 app and see if I can find the culprite

---

### Post by kevinatkins on 2007-11-14
Hi,

I know this thread is quite old, but I thought I'd post a solution to the problem anyway.

I've got an i-Friend nc202-i4 laptop, too, and also experienced this problem...

I finally traced it to buggy APIC routing and the issue can be resolved by adding 'noapic' to your kernel boot options... Then the laptop behaves perfectly!

Hope this helps.

Kevin.

PS - I tried Ubuntu 7.10 on this machine - no-go. 7.04 is fine, though.

---

