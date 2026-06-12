---
title: "software raid performance after upgrade"
date: 2007-08-01
forum: General Help
---

### Post by 241comp on 2007-08-01
After upgrading from Feisty to Gutsy, my software raid 5 performance dropped from ~220MB/sec read to ~45MB/sec read.  No other changes that I know of besides the upgrade.  Any suggestions on what may be causing this significant drop in performance?  Any setting changes that may be causing this?  The read performance for any individual disk is ~70MB/sec so the raid array is significantly slower than the disks that make it up.

---

### Post by fjgaude on 2007-08-01
Gosh, you are brave to be running Gusty and expecting good results at this point in its development.

I get 114MB/sec with my software raid5 3x, 70MB/sec drives, and Feisty. It is limited by the PCI bus (133mb/sec) onto which the SATA controller is part, the ASUS motherboard.

What's your setup to get such high throughput under Feisty?

frank

---

### Post by 241comp on 2007-08-01
I expected some loss of performance as things aren't 100% yet but the drop I'm experiencing is definitely unexpected.  I wonder if this is related to the existing issue with Gutsy and EVMS taking 100% of CPU (I followed recommended procedure and removed evms)?

My array is 5 x 500GB WD RE2.  My motherboard is a S2915A2NRF with 1x Opteron 2214HE and 2 x 2GB RAM.

---

### Post by fjgaude on 2007-08-01
Well, I can't say about EVMS... it's hard to say what Gutsy is like during development stages... I've given up using it because of issues, issues... but when it comes out, released it will be good, just like the dev cycles of Edgy and Feisty... I no longer wish to play with these Alphas.

My CPU is an AMD 64 2X 4400+ with 2G of SDRAM. The MB uses PCI bus to drive the SATA controllers. Are you using the controller on the MB or a PCI-E or -X controller?

And what are you using to test through-put? I'm using hdparm, but do use Bonnie++.

I'm a graphic designer and disk I/O is the last remaining bottleneck for me. Memory and CPU are fast enough, but not the drives.

frank

---

### Post by 241comp on 2007-08-01
I'm using the on-board SATA channels (which I believe are connected through PCI-E).  The quoted throughput is as tested with both hdparm and dd.  The Tyan S2915A2NRF is definitely a good motherboard for performance.  I initially benchmarked >250MB/s with 6 drives (cached reads >2200MB/s).  Since I can't boot from software RAID-5 and didn't have an external controller available, I'm using 5 drives for my array and one as my boot drive.

---

### Post by fjgaude on 2007-08-01
Thanks... my next build will use a board that has high speed SATA controller driven from PCI-E for sure. Of course I could buy a PCI-E SATA card to go into the space slot I have, if I can find such a card. I looked sometime back and all I could find that I knew was fast were the over $300 RAID cards from Areca and the like. I just wanted a serial controller but couldn't find one. I want to stay with Linux software RAID since I know what it does, and how to do what I want with it.

You used something like

 $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

to test throughput, eh?

frank

---

### Post by 241comp on 2007-08-13
Well, I did an apt upgrade to the latest packages (including a new kernel) and the performance is improved significantly (now at ~110MB/s) so I'm hopeful that by the time Gutsy is released, it's back to the 220MB/s I was getting in Feisty.  Anyone have any tweaks I could try to improve my software raid performance?

---

