---
title: "Transfer to another machine to run fstrim on SSD?"
date: 2016-01-06
forum: General Help
---

### Post by QIII on 2016-01-06
I have an Odroid XU4 that boots to an HDD on a USB3 to SATA adapter inside a CloudShell.

I'd like to replace the HDD with an SSD for speed, but fstrim does not work over USB3.

I'm wondering if I could periodically unplug an SSD from the Odroid and put it into a hot-swap bay on one of my other computers and run fstrim on it using that machine.

Does anyone know if that will work?  I don't know if the OS is keeping track of deletions and moves, or if it is all handled by the SSD controller.

---

### Post by QDR06VV9 on 2016-01-06
@QIII See if this is of any use to you
[Can a TRIM capable SSD be used on a non-TRIM system and transferred to a TRIM capable machine for maintenance?]("http://superuser.com/questions/560300/can-a-trim-capable-ssd-be-used-on-a-non-trim-system-and-transferred-to-a-trim-ca")

---

### Post by QIII on 2016-01-06
Not really.  The question of move/trim is not really answered.

That's the sort of answer I've been finding the last few days.

Sigh.

BTW, I'm pretty sure the SSD is blissfully unaware of the file system and that the OS sends the controller instruction about what is mo longer valid.

---

### Post by mc4man on 2016-01-06
The other question would be does the ssd drive take care of trim/garbage collection itself? Both of the usb3 ssd drives I've used *seem* to indicate that they do. My latest one (adata) has been going for over a year now with no apparent slowdown running multiple Os's.
My previous drive (angelbird) listed autotrim as a feature, I believe I totally screwed it up by running a full format on it.
(or something broke down on the drive, I'm thinking the format most likely cause.
 
Edit: i see now you say you're not sure if drive handles.., it was mentioned to me that I could try taking the borked angelbird, put in an enclosure, ect. to run a ATA Secure Erase command on so would imagine you could do the same for trim though I'd leave drive alone if performing well.

---

### Post by QIII on 2016-01-06
Unfortunately, the ATA Trim command does not work over USB3 at present, even if UASP is enabled.  And I don't want to do a secure erase and lose everything then restore from backup.

G/C (often marketed by the misnomer "auto trim") is common, but it's not the same as trim.

---

### Post by sudodus on 2016-01-06
I have an external box where I can put SSDs and HDDs. It has both USB3 and eSATA plugs, and I can connect it via eSATA and get it trimmed.

So my answer is: ***Yes, you can connect your SSD via SATA or eSATA and get it trimmed***.

-o-

I am testing a new USB 3 ***pendrive*** with built-in trim. It is still way too expensive, but soon such pendrives will probably be common and cheap.

[See this link](http://www.kingston.com/datasheets/DTWS_us.pdf)

> SPECIFICATIONS
...
Supports TRIM and S.M.A.R.T commands
...

---

### Post by QIII on 2016-01-06
The problem, however, is this:  the disk will have to be removed from the Odroid to a different machine and connected via SATA.

Are you saying that SSDs from other machines can be trimmed on that machine?

---

### Post by sudodus on 2016-01-07
If the SSD has a root partition with an ext4 file system, and there is a linux operating system without any proprietary drivers, it should be portable and should run also in another computer (which does not need proprietary drivers).

If the system is such that the SSD does not boot in another computer, it should still be possible to connect and run and trim an SSD (at least a 'naked' SSD device) in another computer via SATA or eSATA. But if the SSD is built into a sealed box with only a USB 3 connection, there are problems.

---

### Post by QIII on 2016-01-07
I can take the drive out of the case.  That's not a problem.

The Odroid XU4 is an SBC with an ARM processor that boots initially from a microSD.  That's a hardware design requirement.  But I have the microSD set up to find a bootable partition (/ on the HDD) and immediately turn control over to the OS drive (the HDD) and the boot proceeds as normal from there. So the OS is actually running in all respects as any other would from the OS drive.  In terms of the file system, it is the same as any other Linux file system.

The Ubuntu Server kernel is the ARM version, tuned by HardKernel (which makes the Odroid) to run on the XU3 or XU4 models, which have an octacore ARM processor.  So I doubt it will run on another machine.  Otherwise, I would just plunk it into another machine, boot from it and run fstrim.

I believe the problem is that the OS keeps track of what data is and is not required any longer and sends the SDD controller instructions to reset the erasure blocks as needed.  I am not convinced that the controller has any idea what is and is not valid data absent those instructions from the OS -- and thus removal to another machine would work -- the other machine having no idea what is and is not "good" data.

I was hoping that I was wrong and any old SSD can be plopped into another machine as just a free device and trimmed.

When I first got the Odroid, I was testing it with a small SSD and it ran very fast.  But without being able to trim via USB3, that wouldn't have lasted long.

The original SSD I was using for testing is now in my Fedora laptop.  I suppose I can pull that out, put it in another machine and see what happens.

Not that I am questioning you, of course!  :)

---

### Post by sudodus on 2016-01-08
I think that if you connect the SSD to another computer via SATA or eSATA (booted from that computer's own linux), you should be able to run fstrim. As the manual page states, it discards unused blocks on a mounted filesystem. Unused blocks are blocks that are not associated with any file or directory, which should be independent of how the computer is booted or the drive is connected. And if connected via SATA or eSATA, fstrim should work if the device and the operating system support it :-P

At least I think it is worth trying. I don't see why it should not work.

-o-

If fstrim does not work, you can still use a crude method, that I use successfully on standard USB drives, that are getting slow: 'Wipe the whole device'. Of course it means that I have to restore the system from a backup afterwards, but it does make a pendrive faster, almost to the original speed. See this link

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

