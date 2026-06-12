---
title: "USB flash drive stuck in read-only mode after formatting"
date: 2015-09-12
forum: General Help
---

### Post by md11cf on 2015-09-12
I've been trying to format a USB flash drive that used to have a live image of Linux Mint 17.2 installed on it, but after numerous attempts using both Linux and Windows, the flash drive seems to be stuck in read-only mode when I'm using Linux. It works fine on Windows, but the problem is that I'm trying to copy files between two Linux computers (one running Linux Mint 13 and the other running Ubuntu 14.04).

Here's a brief summary of what I've tried to do so far.

First off, I used the "Disks" tool in Ubuntu 14.04 to format the flash drive. It erased all of the partitions on the drive. I then used the same tool to add a single W95 FAT32 partition spanning the entire flash drive. I tested it by attempting to copy files onto it, but it gave me the following error message:

> Error while copying to "CRUZERBLADE". The destination is read-only.

I happen to have access to a Windows computer, so I mounted the flash drive on Windows and selected "format" (also FAT32). After having formatted the drive, I tested it by trying to copy files to it using Windows. Everything worked fine - until I took it back to my two Linux computers, which gave me the same error message as above.

None of the remedies that I've come across on the internet so far have worked, but here is the output from the ones I've tried:

```

sudo dosfsck -av /dev/sdb1
[sudo] password for ming: 
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSDOS5.0"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
      2322 reserved sectors
First FAT starts at byte 1188864 (sector 2322)
         2 FATs, 32 bit entries
   7794176 bytes per FAT (= 15223 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 16777216 (sector 32768)
   1948431 data clusters (7980773376 bytes)
63 sectors/track, 255 heads
        62 hidden sectors
  15620218 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdb1: 3 files, 3/1948431 clusters

```

```

dmesg | tail
[15018.780105] usb 2-1: new high-speed USB device number 16 using ehci_hcd
[15018.913679] scsi12 : usb-storage 2-1:1.0
[15019.913560] scsi 12:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.19 PQ: 0 ANSI: 5
[15019.914158] sd 12:0:0:0: Attached scsi generic sg2 type 0
[15019.916776] sd 12:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[15019.917922] sd 12:0:0:0: [sdb] Write Protect is off
[15019.917926] sd 12:0:0:0: [sdb] Mode Sense: 43 00 00 00
[15019.918658] sd 12:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[15019.927613]  sdb: sdb1
[15019.930666] sd 12:0:0:0: [sdb] Attached SCSI removable disk

```

I've noticed that the output from the second command (dmesg | tail) states that the write cache is disabled, which I suspect may be the problem. Has anyone got any suggestions as to how I could re-enable it? Thanks.

---

### Post by md11cf on 2015-09-12
Never mind, problem solved. Turns out it was an issue with my computer (with any USB flash drive) rather than with the flash drive itself, solved by a simple reboot.

---

### Post by Mike_Walsh on 2015-09-12
Mmm. I, unfortunately, now have this same problem, too.

My elderly Compaq Presario desktop PC used to be able to boot from FAT32-formatted flash drives. But after upgrading from a single-core Athlon 64 to a dual-core Athlon 64 X2 (and to be able to run this, needing to re-flash the BIOS with a newer version), the new BIOS refuses to recognise FAT32 at boot time. Bummer. I used to enjoy running KolibriOS from flash drive; Kolibri **will only run** in a FAT32 partition!

It won't even run from the CD, either. Marvellous, ain't it?

(I was also going to say that if you've got a 16 GB Cruzer 'Blade', there's been an on-going problem with them going 'read-only' for the last 3-4 years. SanDisk's answer to the problem is that there **is **no answer; send it back to them, and they'll send you a new one to replace it. I believe the problem essentially stems from a duff batch of flash chips they got from chip manufacturers Hynix, back in 2012... There's page after page of irate posts on the SanDisk Forums concerning this very issue.)

But yours would appear to be an 8 GB. I've been using these 'Blades' for a few years, and most of mine are 8 GB, with a couple of 32 GB models, too. I do hope this isn't a sign of 'things to come'!

Maybe I've just been lucky, so far.....


Regards,

Mike. ;)

---

### Post by md11cf on 2015-09-12
Sorry to hear it. It turns out it really wasn't an issue with the Cruzer Blade at all but more of a temporary problem that my computer was having with USB flash drives in general. I found that out after borrowing a friend's 32 GB drive and it turned out to have the same problem. But quite curiously the problem went away after rebooting. So, this shouldn't be a sign of things to come!

---

### Post by sudodus on 2015-09-13
Hi Mike,

> **Mike_Walsh said:**
> Mmm. I, unfortunately, now have this same problem, too.

My elderly Compaq Presario desktop PC used to be able to boot from FAT32-formatted flash drives. But after upgrading from a single-core Athlon 64 to a dual-core Athlon 64 X2 (and to be able to run this, needing to re-flash the BIOS with a newer version), the new BIOS refuses to recognise FAT32 at boot time. Bummer. I used to enjoy running KolibriOS from flash drive; Kolibri **will only run** in a FAT32 partition!

It won't even run from the CD, either. Marvellous, ain't it?

In some computers it helps to add the boot flag to the FAT partition. It should not be necessary for linux, but sometimes it helps anyway.

Kolibri is easier for me to boot from CD. It's funny how different computers interact with the software :-)
> 
(I was also going to say that if you've got a 16 GB Cruzer 'Blade', there's been an on-going problem with them going 'read-only' for the last 3-4 years. SanDisk's answer to the problem is that there **is **no answer; send it back to them, and they'll send you a new one to replace it. I believe the problem essentially stems from a duff batch of flash chips they got from chip manufacturers Hynix, back in 2012... There's page after page of irate posts on the SanDisk Forums concerning this very issue.)

But yours would appear to be an 8 GB. I've been using these 'Blades' for a few years, and most of mine are 8 GB, with a couple of 32 GB models, too. I do hope this isn't a sign of 'things to come'!

Maybe I've just been lucky, so far.....


Regards,

Mike. ;)

Maybe those blades were particularly vulnerable to 'gridlocking'. See these links.

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only 'gridlocked', then totally 'bricked'.

---

### Post by Mike_Walsh on 2015-09-13
Hi, sudodus.

Mm. Maybe. The strange thing is, that I've tried not just the 'Blades' (of which I have several), but also a TDK, and a couple of old Kingstons. In every single case, when formatted to ext 2 (or ext3, or 4) they will invariably boot with no problems. But with FAT32 formatting, the old girl doesn't recognise any of them. And the boot flag was definitely set.

Which leads me to think it's something to do with the new BIOS.

Things are a bit of a hodge-podge at the moment..! The MSI MS-7184 ('Amethyst M') mobo in her will support my 'new' Athlon X2 CPU.....but HP (who provide the support for them) can't supply a sufficiently new BIOS that will support the dual-core processor. Accordingly, an acquaintance of mine on the Puppy Forums did some research for me (without being asked to), and found out that MSI make another board called the MS-7093.....which is, to all intents and purposes, identical to the 7184 except for having 4 SATA ports, rather than the 2 that mine has. Same chipsets, controllers, CPU socket and everything.

Accordingly, with a wee bit of trepidation, I downloaded the newest BIOS available for it (2006!!), and with my friend's help (from 3500 miles away.....ain't the Internet a **wonderful **thing! :D), we flashed the new BIOS to the WinBond EEPROM; I fitted the 'new' CPU, and...it works perfectly. Has been doing so for the last 4/5 months. now.

(My friend spent a year or two working in a computer repair shop somewhere in North Carolina when he was younger, and the biggest part of his work involved flashing new BIOSes to customer's machines in preparation for system upgrades. So it's fair to say he's had a bit of practice..!)

The upshot of all this is that the system now thinks it's a 7093 board, rather than a 7184. Yet despite all the warnings from HP about never using a BIOS direct from the manufacturer (MSI), as you run the risk of 'bricking' your machine, this is the only 'side-effect' that I've come across.

As part of his research,  he found out that a lot of people have carried out this very 'upgrade' on this same board over the last decade, and in every single case that he could find, it was a complete success. Which is why he was fairly confident in suggesting it to me in the first place..! :)

Still doesn't explain why I can't get Kolibri to boot from CD, especially since I had it running fine on here **before** the 'upgrade'.....

Any ideas, at risk of 'hijacking' this thread any further ? (Although, since the OP has declared his problem 'solved', maybe it isn't; you're one of the 'mods'...you tell me!)

**BTW**: I meant to say in the previous post that it was a batch of faulty **controller** chips from Hynix.....not the flash chips themselves.


Regards,

Mike. ;)

---

### Post by sudodus on 2015-09-13
> 
(BTW: I meant to say in the previous post that it was a batch of faulty controller chips from Hynix.....not the flash chips themselves.)

You are right, I misunderstood that bit of information :-)

---

