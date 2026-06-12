---
title: "Recovering data from SD card.. cannot even mount"
date: 2007-11-19
forum: General Help
---

### Post by distolin on 2007-11-19
Hi,

One of my SD cards has failed, and I'm hoping to recover as much of the data as possible.  I've seen a few utilities out there, but unfortunately cannot even mount my SD card to kick off any recovery process.  I have an external card reader which can successfully load other working SD cards.  Relevant output below.  Any ideas?  Would be very much appreciated.  Thanks.

[Trying to mount results in failure]
**$ sudo mount /dev/sdd1 /mnt/sd/**
mount: No medium found

[This fails too]
**$ dd if=/dev/sdd1 of=home.img bs=512**
dd: opening `/dev/sdd1': No medium found

[Output from 'dmesg'... it looks like it can recognize something, but fails somewhere in the process]
**$ dmesg**

[ 3552.204000] sd 4:0:0:2: [sdd] 3910656 512-byte hardware sectors (2002 MB)
[ 3552.204000] sd 4:0:0:2: [sdd] Write Protect is off
[ 3552.204000] sd 4:0:0:2: [sdd] Mode Sense: 03 0000 00
[ 3552.204000] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[ 3552.204000] sd 4:0:0:2: [sdd] 3910656 512-byte hardware sectors (2002 MB)
[ 3552.208000] sd 4:0:0:2: [sdd] Write Protect is off
[ 3552.208000] sd 4:0:0:2: [sdd] Mode Sense: 03 00 00 00
[ 3552.208000] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[ 3552.208000]  sdd: sdd1
[ 3556.828000] sd 4:0:0:2: [sdd] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3556.828000] : Add. Sense: Medium not present
[ 3556.828000] end_request: I/O error, dev sdd, sector 601
[ 3556.828000] printk: 44 messages suppressed.
[ 3556.828000] Buffer I/O error on device sdd1, logical block 472
[ 3556.840000] sd 4:0:0:2: [sdd] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3556.840000] : Add. Sense: Medium not present
[ 3556.840000] end_request: I/O error, dev sdd, sector 602
[ 3556.840000] Buffer I/O error on device sdd1, logical block 473
[ 3556.840000] Buffer I/O error on device sdd1, logical block 474
[ 3556.840000] Buffer I/O error on device sdd1, logical block 475
[ 3556.840000] Buffer I/O error on device sdd1, logical block 476
[ 3556.840000] Buffer I/O error on device sdd1, logical block 477
[ 3556.840000] Buffer I/O error on device sdd1, logical block 478
[ 3556.840000] Buffer I/O error on device sdd1, logical block 479
[ 3556.840000] Buffer I/O error on device sdd1, logical block 480
[ 3556.840000] Buffer I/O error on device sdd1, logical block 481

---

### Post by az on 2007-11-20
Try gnu-ddrescue.

sudo ddrescue /dev/sdd image log

That will attempt to read the device to an image file.  Now what gnu-ddrescue can do that other tools can't is keep reading past errors.  However, if the controller chip in your card is borked, there is nothing you can do using any software tool.


Once you get an image, you can try to mount it or fix the filesystem.  If that fails, you can try to carve to files out using foremost or photorec.

See
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by distolin on 2007-11-20
Thanks for the tip, but it looks like it is still failing:

**$ sudo ddrescue /dev/sdd image log**
ddrescue: cannot open input file: No medium found

What do you think I should do?

---

### Post by az on 2007-11-20
I would say your only hope is to see if you can get a read from a different card reader.

---

### Post by malfist on 2007-11-20
does ddrescue work for flash drives too?

---

### Post by distolin on 2007-11-20
Actually, wow, I got it to work.  I still don't know what the problem was, but I noticed that right after inserting the card, if I try to mount immediately, the process would take a little longer to fail, as if there was some reading going on.

So, what I did was run ddrescue immediately after inserting the card.  The first time I did this I was able to get a rescue image of a few hundred kb, but timing it correctly the second time, I think I pretty much got all of my pictures back.  They were from my last trip to Cancun, so I'm very happy to have them again.

Thanks a bunch, az!  ddrescue was a big help, and so were you.  My utmost thanks!

---

