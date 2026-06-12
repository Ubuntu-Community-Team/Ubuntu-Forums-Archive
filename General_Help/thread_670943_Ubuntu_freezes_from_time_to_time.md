---
title: "Ubuntu freezes from time to time"
date: 2008-01-18
forum: General Help
---

### Post by pencilcheck on 2008-01-18
When my Gusty freezes, I went to the systemlog and found this repeating logs which I suspect to be the reason. But I have no clue for what it's saying. What shoud I do to stop Gusty freezing from time to time?:confused:
> 
Jan 18 00:17:00 arma-laptop kernel: [ 2315.476000] ata1.01: qc timeout (cmd 0xa0)
Jan 18 00:17:11 arma-laptop kernel: [ 2315.476000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Jan 18 00:17:11 arma-laptop kernel: [ 2320.516000] ata1: port is slow to respond, please be patient (Status 0xd0)
Jan 18 00:17:11 arma-laptop kernel: [ 2325.500000] ata1: device not ready (errno=-16), forcing hardreset
Jan 18 00:17:11 arma-laptop kernel: [ 2325.500000] ata1: soft resetting port
Jan 18 00:17:11 arma-laptop kernel: [ 2325.860000] ata1.00: configured for UDMA/100
Jan 18 00:17:11 arma-laptop kernel: [ 2326.048000] ata1.01: configured for UDMA/25
Jan 18 00:17:11 arma-laptop kernel: [ 2326.048000] ata1: EH complete
Jan 18 00:17:11 arma-laptop kernel: [ 2326.056000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jan 18 00:17:11 arma-laptop kernel: [ 2326.064000] sd 0:0:0:0: [sda] Write Protect is off
Jan 18 00:17:11 arma-laptop kernel: [ 2326.080000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 18 00:17:11 arma-laptop kernel: [ 2326.096000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Jan 18 00:17:11 arma-laptop kernel: [ 2326.104000] sd 0:0:0:0: [sda] Write Protect is off
Jan 18 00:17:11 arma-laptop kernel: [ 2326.492000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


---

### Post by anthonyJC on 2008-01-18
its says your hdd went to sleep in a bad way. turn off power saving in bios (not acpi related). its forcing your hard drive to spin down when ubuntu expects it to still be spinning, so when it accesses it, it takes too long since it has spun down and ubuntu thinks its bugged firmware and so hard resets it.

---

### Post by pencilcheck on 2008-01-18
I went to my BIOS and see nothing related to power saving. My BIOS is old. By the way, I'm using ASUS Laptop. However, I see some options for my IDE Configuration I would like to show and  maybe one of them is the power saving option which disguised with different names.

BIOS | Advanced | IDE Configuration | Primary IDE Master | ----->
LBA/Large Mode        [Auto]
Block                          [Auto]
PIO Mode                   [Auto]
DMA Mode                 [Auto]
S.M.A.R.T.                  [Auto]
32Bit Data Transfer   [Enabled]

Which one should I turn off?

Or is it too old that i have to update my bios?

---

### Post by anthonyJC on 2008-01-18
none of them is for power and if there is not power saving in your bios your hard drive is not being spun down by your bios. next thing to try is use smart software to check smart status of the drive. it will tell you if the hard drive is failing or bad.

---

### Post by pencilcheck on 2008-01-18
One of my friend gave me a Diagnostic CD called "Quick something" to scan my system for errors, but it came out surprisingly that there is no error on any of my hardware.

Now what should I do? I don't think my hd is faulty since it can run vista perfectly, no crashes and freezes.

---

### Post by anthonyJC on 2008-01-19
in this thread [http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825) post #5, it talks about decreasing the amount of times ubuntu spins the drive down ,it should decrease the probability of your problem occuring. can you hear your hd spin down and does it have some correlation to the time the freeze occurs.

---

### Post by pencilcheck on 2008-01-21
Well, it didn't work, my Laptop still freezes.

I will try to remove my CDrom drive and see what happens.

---

### Post by pencilcheck on 2008-01-21
Hey! After I removed my CDrom drive, nothing is stopping me now, no more freezes!!!!
But I want my cdrom drive back:(
What should I do?
Why is my cdrom drive freezing ubuntu up?

---

### Post by photismos on 2008-02-22
I suspect ACPI problems here so I'm going to cut-paste a potential solution that worked for me.  It's a follows: 

I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

### Post by kiev on 2008-05-24
This kernel bug
 this problem already whole year

for me she showed up one time in the floor of hour, however as a result of this problem I lost a mysql database - mysql innodb not start - "Accertion error" - did not help even "innodb_force_recovery = 4", backup was an a week remoteness - the works of whole department lost data for a few days, the management simply in shock - I going to discharge from job (((

this problem already whole year:
-----------
I'm stumped trying to track down the below intermittent problem.....
I've confirmed this problem on 2.6.19, 2.6.20 and 2.6.21.
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765)
[http://kerneltrap.org/node/16175](http://kerneltrap.org/node/16175)
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

SUSE:

ata errors, system freeze
[https://bugzilla.novell.com/show_bug.cgi?id=393675](https://bugzilla.novell.com/show_bug.cgi?id=393675)

System lockup with concurrent acces to SATA disks on Promise PDC20378
[http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html](http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html)

Kernel panic / system hang / sata_promise
[https://bugzilla.novell.com/show_bug.cgi?id=350907](https://bugzilla.novell.com/show_bug.cgi?id=350907)

DELL Poweredge 2970 hangs sometimes (ata1)
[https://bugzilla.novell.com/show_bug.cgi?id=359333](https://bugzilla.novell.com/show_bug.cgi?id=359333)

Fedora:
ata device crashing system in Fedora 8
[http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html](http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html)

problème de mise à jour
[http://forums.fedora-fr.org/viewtopic.php?pid=253930](http://forums.fedora-fr.org/viewtopic.php?pid=253930)

Kernel 2.6.24.x boot problem - Anyone , Any idea
[http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10](http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10)

Thought though with the newest hard drive with support of NCQ such is not present, ... also same:

"With this kernel I’m getting frequent temporary freezes (system comes back responsive after a minute or so…)."
[http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296](http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296)

---

