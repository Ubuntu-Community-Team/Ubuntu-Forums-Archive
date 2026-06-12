---
title: "Lubuntu Won't Load on Windows 7 Computer"
date: 2015-09-25
forum: General Help
---

### Post by quaesitor2 on 2015-09-25
I have been trying to fix my windows 7 computer which has come down with a nasty case of windows update interrupt instigated bsod. I was advised to download lubuntu 32-bit and create a live cd, and boot from that. 

the version of lubuntu is 15.04.

the hash checked out, I proceeded to iso burn a dvd-r using a mac and an external dvd writer. Upon finishing the burn I got an "unreadable" message which caused the disk to eject. I then put the disk into an external dvd writer attached to the windows 7 computer. the computer then began to go back and forth between the vaio logo and a screen with the message:

 [I]isolinux 6.03 20150318 ETCDisolinux: found something at drive = A1
isolinux: looks reasonable, continuing…
isolinux:  Disk error 01,  AX = 425B, Drive A1[/I]


What does this mean and how do I get the disk to boot so I can begin repairing my windows computer in earnest.

---

### Post by efflandt on 2015-09-26
Does the Mac burning software have a setting to "verify" a disc after writing it. While it is normal for a disc to eject after being written, the "unreadable" error may mean that something was unsuccessful, which may be the reason it will not boot.

Are you sure that the drive and everything is compatible with DVD-R? My PC from 2004 could write DVD+R, but not DVD-R and I forget which type I had trouble with when attempting to write recovery discs when I bought my current PC in 2010. I usually use a USB memory stick (or SD card in USB card reader) to boot live/install iso from, but that is easy for me because I have "Startup Disk Creator" in Ubuntu on more than one computer.

---

### Post by quaesitor2 on 2015-09-26
> **efflandt said:**
> Does the Mac burning software have a setting to "verify" a disc after writing it. While it is normal for a disc to eject after being written, the "unreadable" error may mean that something was unsuccessful, which may be the reason it will not boot.

Are you sure that the drive and everything is compatible with DVD-R? My PC from 2004 could write DVD+R, but not DVD-R and I forget which type I had trouble with when attempting to write recovery discs when I bought my current PC in 2010. I usually use a USB memory stick (or SD card in USB card reader) to boot live/install iso from, but that is easy for me because I have "Startup Disk Creator" in Ubuntu on more than one computer.

Yes, I checked the verify option. The external drive is indeed compatible with DVD-R, it is a samsung DVD-Writer, I was able to boot the disk on my mac after rebooting while holding the op key down. Although the lubuntu menu has a tendency to freeze while I scroll through the options.

---

### Post by timotheus3 on 2016-01-14
do you have a USB drive handy? i find its easier and faster, or alternatively a rooted android with drive droid.

---

### Post by mastablasta on 2016-01-14
> **quaesitor2 said:**
> Yes, I checked the verify option. 

it means it was a bad burn. data on Disk didn't match (bit-by-bit) to the data on your PC/Mac whatever.

try again or use a USB (an 8 GB one costs 4 or 5 EUR here)

---

