---
title: "Kernel Panic!! Help!!"
date: 2007-07-23
forum: General Help
---

### Post by oolunchbox on 2007-07-23
My wife's comouter has been acting up as of late and the other day we had our power go off. When I tried to turn her compputer back on the screen would freeze at the very begining of the progress bar.  I rebooted and switched to recovery mode to see what the problem is and fourn that the computer is freezing at:
```

[  24.233569] ata5: SATA link down (SStatus 0 SControl 310)
[  24.233639] scsi6 : sata_sil
[  24.244380] attempt to access beyond end of device
[  24.244420] hda1: rw=0, want=233237400, limit=229825827
[  24.244460] attempt to access beyond end of device
[  24.244499] hda1: rw=0, want=233237376, limit=229825827
/sbin/init: error while loading shared libraries: /lib/libc.so.6: cannot rread file data: Input/output error
[  24.244926] Kernel panic - not syncing: Attempted to kill init!
[  24.244966]

```
 She's running fiesty with the 2.6.29-16-generic kernel

System is:
AMD Athlon 64 3200+
1GB PC 2700 DDR
ASUS K8N-E DELUXE Motherboard
and 2 hard drives
a WD 120 GB and 160GB

I've had a couple hard drive errors before that fsck was able to fix but I cannot even get the machine booted to run fsck. I really just need to be able to salvage the data on the hard drive I can reinstall without an issue as long as I can get the data off that drive.

Can anyone help?

---

### Post by heimo on 2007-07-23
Use Live-CD to boot, then mount disks and make backups (to external drive or from one drive to the other). During reinstall, make sure you're not formatting your backups. :)

---

### Post by kevinlyfellow on 2007-07-24
> **heimo said:**
> Use Live-CD to boot, then mount disks and make backups (to external drive or from one drive to the other). During reinstall, make sure you're not formatting your backups. :)

Or you could also use the live-cd to fsck and see if that works.

---

### Post by heimo on 2007-07-24
> **kevinlyfellow said:**
> Or you could also use the live-cd to fsck and see if that works.

Yeah. But I must elaborate what I meant. He probably wants to get rid of that drive which seems to be failing. It could be just random problems with filesystem, but sounds a lot more like hardware failing. Backup first, investigate later.

---

### Post by Claus7 on 2007-07-24
Hello,

I know that you might have a lot of things in your mind right now on how to fix this or that. What I would propose you to look first is your memory. I had exactly the same message (kernel panic), I removed my memory, cleaned it, replaced it back and everything was ok. 
Of cource from the message you provide it seems that it might be a hard drive problem. I do not think that my proposal will be time consuming and so difficult for someone to try.
I have to say that even when I had bought my computer some years back, I was facing boot problems because the memory wasn't placed correctly.

Regards!

---

### Post by oolunchbox on 2007-07-26
Thanks Everyone!
I managed to mount the drive using the LiveCD and verify that I could salvage all the data I needed. I had a spare 200GB drive laying around so I just did a fresh install on that drive and copied my data.

Thanks again!

---

