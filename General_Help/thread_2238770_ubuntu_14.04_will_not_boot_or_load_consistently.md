---
title: "ubuntu 14.04 will not boot or load consistently"
date: 2014-08-10
forum: General Help
---

### Post by Paperfairy on 2014-08-10
Clean install of ubuntu 14.04... upon first boot, all is well. No problems to report. On the 2nd log in, is where trouble begins. Sometimes (no particular pattern), the computer will get to the log in screen. Sometimes, the ubuntu loading screen never resolves. When it DOES load:

1. Unity does not load anything in its search or applications lists. Unity will open, but nothing occurs.
2. Terminal does not respond to commands. Terminal windows (and even TTY1-6) do absolutely nothing when commands are issued.
3. Left side taskbar "works", and launches tasks, but they quickly freeze and need to be force quit to get rid of them.
4. Desktop background does not and will not load.

I have done the following tests so far:

* Deleted all settings in /home partition to ensure this was not the problem

* Tried to narrow down if an app was misbehaving - on the latest iteration, only installed chrome and vlc, problem still occurs.

How should I proceed?

---

### Post by ajgreeny on 2014-08-10
Are you certain the .iso file you used to install was a good one; did you check the [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") ?

What hardware are you using?

---

### Post by Paperfairy on 2014-08-10
I'm redownloading and I'll check the hash.

My build is:

**CPU:** [AMD FX-4300 3.8GHz Quad-Core Processor](http://pcpartpicker.com/part/amd-cpu-fd4300wmhkbox)
**Motherboard:** [Gigabyte GA-78LMT-USB3 Micro ATX AM3+ Motherboard](http://pcpartpicker.com/part/gigabyte-motherboard-ga78lmtusb3) 
**Memory:** [Kingston HyperX Blu 8GB (2 x 4GB) DDR3-1333 Memory](http://pcpartpicker.com/part/kingston-memory-khx1333c9d3b1k28g)
**Storage:** [Sandisk Ultra Plus 64GB 2.5" Solid State Drive](http://pcpartpicker.com/part/sandisk-internal-hard-drive-sdssdhp064gg25) (windows)
**Storage:** [Western Digital Caviar Blue 1TB 3.5" 7200RPM Internal Hard Drive](http://pcpartpicker.com/part/western-digital-internal-hard-drive-wd10ezex) (linux)
**Video Card:** [MSI R7 260X 2GD5 OC Radeon R7 260X 2GB 128-Bit GDDR5 PCI Express 3.0 HDCP Ready CrossFireX Support Video Card](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127762)

---

### Post by oldfred on 2014-08-11
Which video driver are you using?
open (Gallium3D) and closed-source (Catalyst) driver

   AMD Radeon R9 290 On Ubuntu 14.04 With Catalyst Can Beat Windows 8.1
 the open-source AMD Hawaii support remains broken,
[http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1)
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)

      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

