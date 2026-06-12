---
title: "[Ubuntu 18.10] USB copy slows down?"
date: 2018-12-26
forum: General Help
---

### Post by Lasakro on 2018-12-26
There was a previous question posted for 16.04 vs 18.10 with nothing clear as to if the answers provided solved the problem so I ask it again. I've never had speedy results after starting my Linux experience with Ubuntu Studio 15.10. I have found that USB Ports do get "contaminated" using Linux after a couple of USB flash drive ejects so my test below was after a cold boot.

So today on Ubuntu Studio 18.10 I have a 32GB Lextar USB 2.0 stick using GPT table and formatted to ext4. I start to copy a 24GB folder of music from a Asus Crosshair Vi Hero, X370 chipset, running a Ryzen 7 1800X through it's USB 3.0 front panel connections (Wire adapter to two USB-A).

Transfer starts at 400MB/s and after one minute drops to 2MB/s. It drifts up to 10 then settles out at 1.5 for the remaining transfer. One thing for sure is that there is very poor core sharing. The load continuously rotates between the 8 cores but only one at a time peaking.

Is there a solution out there?

---

### Post by Lasakro on 2018-12-28
It was [suggested here]("https://ubuntuforums.org/showthread.php?t=2408292") that the problem could be by using an interim release. I installed a fresh copy of 18.04 will all the updates, same USB slowness.

---

### Post by TheFu on 2018-12-29
The best real-world performance I've ever seen from any USB2 flash device is about 22 Mbps.  There are hundreds of variables which go into the write performance, after the physical limitations of the flash device itself, the most important would be the USB chip used, then the bus speed inside the motherboard and the path that the data is taking between the source and the target.

The initial speed is from disk buffers.  You can watch it with the 'free -hm' command.

Might want to use f2fs instead of ext4. Journal'ed file systems are hard on flash storage. Over time, performance will get slower and slower as the cells begin failing.

BTW, whenever disk or network performance is discussed, Mbps is normally used to prevent the conversion and mistakes by using MBps.  Sorta like choosing to use metric system instead of the English measurement system. 

If you need better performance, get a USB3 flash device.  However, if this device is used to transfer files constantly, daily, filling the available storage, then expect it to fail in 1-2 yrs.  I've seen this with quality flash storage that died completely before even 1 yr was up.  We were using it with some video recording equipment because it was convenient.  

After burning through a few of those 64G devices, we decided to switch to spinning disks.  We've been using a $9 250G WD Blue disk for the last 2 yrs without any issue.  But I suspect your usage pattern is different from ours.

Bad performance with USB2 flash devices has been reported on Windows too.

---

### Post by Lasakro on 2019-01-01
Good information, thanks. I switched from ext4 to f2fs and received better performance. Rates went from 2 to 7. I've now realized that there is a tremendous difference between the specification and real would experience. I've ordered a 3.1 flash drive to try next.

---

### Post by oldfred on 2019-01-02
I switched to USB3 years ago, when the MicroCenter store near me dropped prices to only a $1 more than USB2. And found USB3 flash drive in USB2 port was about 10% faster.

Store is only 2 or 3 miles away, and every time I go there, the flash drives on wall behind cash registers are either lower in cost, faster, or larger (and lower in cost). Just purchased new 128GB USB3. Did full install of Ubuntu and have been frustrated with slowness.
Realized I had rebuild system years ago into old case that had no USB3 ports on front. Have been using cable. Decided to try plugging directly into USB3 port.

       fred@bionic-z97:~$ sudo hdparm -Tt /dev/sdd
/dev/sdd: new 128GB flash drive USB3 Jan 2019 connecting cable
 Timing cached reads:   26016 MB in  1.99 seconds = 13047.34 MB/sec
 Timing buffered disk reads: 122 MB in  3.03 seconds =  [COLOR=#ff0000]40.26 [/COLOR]MB/sec

fred@bionic-z97:~$ sudo hdparm -Tt /dev/sdd Direct into port
/dev/sdd:
 Timing cached reads:   27916 MB in  1.99 seconds = 14002.61 MB/sec
 Timing buffered disk reads: 352 MB in  3.02 seconds = [COLOR=#ff0000]116.72[/COLOR] MB/sec 


Cannot tell you how many posts in forum on making sure you have good connections/cables. Some even by me. :)

---

