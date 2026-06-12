---
title: "Secondary HD (Ubuntu) not recognized at all after migrating to a HD enclosure"
date: 2014-09-06
forum: General Help
---

### Post by send2 on 2014-09-06
Hello all,

I have 2 hard drives that are running on a Toshiba satellite-A505 laptop. My primary drive is the original drive (windows), my external is Ubuntu. Everything was ok until I decided to enclose the second drive to prevent dust from settling on it. The enclosure is a Sabrent IDE/SATA 3.5" hard drive case with a 2.0 USB connection. 

Now it is not being recognized at all. It is connected to my laptop via a USB cable. The original configuration (without the case) I had it running under was connecting the secondary drive to my laptop via an esata cable, all was fine. Seems like grub2 was overwritten?

I used gparted to look at all my drives via live cd and my windows drive is recognized but not my Ubuntu drive, it is being see as unallocated. There is an exclamation point that when open says: warning: can't have a partition outside of the disk! 

 I also checked thru sudo fdisk -l and windows drive is there but for ubuntu drive it said "unable to seek on /dev/sdb: Invalid argument."

Is there anyway of rescuing this hard drive? I am writing this post from my windows drive. As a curiosity under windows I check to see what i would see under computer and it shows a hard drive E but it wants to format it. 

Any info at all would be great. I miss Ubuntu.

Note: I forgot to mention that i changed in BIOS the order of boot so i could boot up my Ubuntu drive, that is when i noticed that nothing happened.

I found the solution: the case that I used had only a usb cable and on a hunch i bought an esata to esata cable to connect external drive to laptop. I changed again the BIOS settings and my laptop booted up in Linux. From what I recently learned, sometimes it is better to go with a esata cable (if it can be used) as the data is transmitted faster. I had the correct boot up settings for both windows and linux but the data was not being trasmitted effectively. Good thing that I didn't have to do more. I learned from this experience however.

---

