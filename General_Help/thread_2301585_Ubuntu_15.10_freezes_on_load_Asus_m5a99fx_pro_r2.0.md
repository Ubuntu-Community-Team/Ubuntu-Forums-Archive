---
title: "Ubuntu 15.10 freezes on load Asus m5a99fx pro r2.0"
date: 2015-11-03
forum: General Help
---

### Post by wiljakson1 on 2015-11-03
I had a MSI 970-g43 mono. It crashed. I just bought and installed an Asus m5a99fx pro 2.0. I can get both windows partitions to load. I have turned off fast boot in is and bios. Changed to other os  instead of windows uefi. I have Ubuntu as dual boot after windows 8.1 on one of my HDD. I have 4 HDD. I cannot get Ubuntu to load from HDD or live DVD. Either way it freezes half way through. Any help would be great. Thanks

---

### Post by Killcycler on 2015-11-16
Hi Wil,I have the same issue with the m5a99fx 2.0. Ubuntu 15.10 simply will not boot.The first issue that caused it to freeze immediately and i couldn't get verbose even happened to be my secondary video card so i removed it. I had a Nvidia 660 and 460 dedicated to remoteFX in server 2012 which is a little uncommon anyhow.The semi-freeze after that complains about the NTFS partition with copied from another post:Failed to mount '/dev/sdb5': Operation not permittedThe NTFS partition is in an unsafe state. Please resume and shutdownWindows fully (no hibernation or fast restarting), or mount the volumeread-only with the 'ro' mount option.What truly strange about this is I'm certainly not hibernating the computer as i restart and i don't even have a hiberfile.sys as i removed it previously with  powercfg -h off.After reading through some other posts for this error they suggest turning off fast boot in windows power options and not so much in the UEFI which ill try later, but i would suggest you try it as well. Google the error and you may come up with other ideas...ill let you know what i find out!

---

### Post by Killcycler on 2015-11-16
Ok...so this site converted my return into nothing and theres a not-so fancy wall of text... I also can't edit that...sorry guys...

---

### Post by Killcycler on 2015-11-17
Ok so i found a few interesting things regarding this.
A-fast boot was still on causing the NTFS error described above. My bad.
B-This freeze occasionally causes a "overclocking failed" notice upon next boot even when not overclocking and
C-The RAID controller also creates the same NTFS error.

By getting through all that with all what i would call valid errors i get to another freeze upon starting this:[https://www.dropbox.com/s/2o20gdcj6bgg0h5/2015-11-16%2015.39.05.jpg?dl=0](https://www.dropbox.com/s/2o20gdcj6bgg0h5/2015-11-16%2015.39.05.jpg?dl=0)

I really don't know what to make of that. On this particular session/attempt i had all devices disabled. Network, audio, serial, usb 3....etc. and some basics setup such as AHCI sata mode, no OC...

I did however find this and that ASM1061 IS the sata controller in the m5a99fx pro 2.0:
[http://askubuntu.com/questions/228927/boot-failure-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/boot-failure-failed-command-identify-packet-device)

The suggestion is worth a shot...

---

