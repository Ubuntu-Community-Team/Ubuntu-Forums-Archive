---
title: "Mount Windows raid in Ubuntu"
date: 2014-11-06
forum: General Help
---

### Post by paulofcorinth on 2014-11-06
Hello all,

I have an issue I am hoping you can help me with. I am working on a PC for a user trying to recover some data. Here is what I know:

There are three hard drives setup in a raid formation either 0 or 5. Not sure which one but I do know that it is striped.

The OS that is on it is Windows XP.

What I don't know:

I do not know the order they are supposed to go in (I have been told it is important to know for Windows. I don't know if it is the same for Linux)

Whether it is hardware or software raid

Variables:

I am using a PCI card to access the SCSI drives. The ribbon doesn't attach to the mono so this is my only option. It is quite old and the only Windows drivers I can find appear to be for Windows XP.

Issue:

The 3 drives were in a Windows XP machine setup in raid 0 or 5 and the mother board was fried due to blown capacitors. The person who brought it to me knew very little except that they needed their data. Can someone help me determine if it is hardware or software raid, the type of raid, then tell me how to extract the data? I am experienced with Linux having taken a couple classes in college and building an Ubuntu server. Also, can this be done without losing the data? 

Thank you in advance.

---

### Post by TheFu on 2014-11-10
Windows RAID is not compatible with Linux RAID. Any recovery, if even possible, must happen through that other OS.

---

### Post by WinEunuchs2Unix on 2014-11-10
> **TheFu said:**
> Windows RAID is not compatible with Linux RAID. Any recovery, if even possible, must happen through that other OS.

That's a blanket statement.

It's not true on this platform.  Intel OROM Rapid Storage Technology using RAID 0 (striped) and Smart Reponse Technology (cache) under Windows 7 whilst using dmraid under Linux (Ubuntu 14.04 / Kernel 3.17.1) and EnhanceIO cache in Linux.

You should rephrase your claim to say which particular Windows RAID and which particular Linux RAID (there are 10? supported by dmraid) are not compatible.

Additionally there is mdraid, mdadm raid, lvm raid and soon (if not now) btrfs raid in Linux.

There *could be* 63 million PC's with Intel OROM RAID / BIOS RAID / Fake-Raid / Raid 0 / Striped Raide based on Intel motherboards with i7 quad cores (like this one) made after mid-2012.

You could be right that his Windows RAID is incompatible with Linux RAID but without more information you could be wrong.

---

### Post by TheFu on 2014-11-11
Don't forget zfs RAID ... but none of that information will help the OP. Clearly you have the greater knowledge and would be better helping, since I don't think he can recover anything using Linux on a system using Windows RAID drivers - ok - perhaps he can recover something, but it won't be fun or profitable. Best to "cut bait" and move on, IMHO.

You know - backups really do make life easier. This doesn't help the OP, since he's trying to help a customer and certainly already knows this.

---

### Post by paulofcorinth on 2014-11-15
Thank you everyone. I found this post that I tried [http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653) but it turns out that this option doesn't work with raid 5. I ended up using ReclaiMe Raid Recovery and got all of his files back for him. ReclaiMe is fantastic and can figure out your raid no matter if it is software or hardware raid. It can create a VHD but I was never able to mount it or extract the files from it. The customer ended up having to purchase the add-on ReclaiMe File Recovery for $80 bucks. Still a small price compared to Best Buy wanting 1,500. Thanks again everyone.

---

### Post by TheFu on 2014-11-16
For anyone else reading ... **ReclaiMe Raid Recovery** is free (the core?), but not open source. It only runs on Windows. 

Having good backups is the cheapest way to avoid this issue completely. RAID is never a substitute for backups.

---

