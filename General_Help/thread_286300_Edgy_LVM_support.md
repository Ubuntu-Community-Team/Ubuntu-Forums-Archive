---
title: "Edgy LVM support?"
date: 2006-10-27
forum: General Help
---

### Post by AusIV4 on 2006-10-27
I've been having a fit getting Edgy to work. Shortly after it came out, I tried to follow Ubuntuguide.org's upgrade directions. I got errors that the package manager couldn't contact a repository. The next several times I booted the system, it froze at the kubuntu boot screen. 

Then I downloaded the install CD and tried to install from that. One of the first things I wanted to do was back up my root file system to my home partition, which is a RAID/LVM combination. I found that the Edgy Live CD wasn't recognizing my (software) RAID devices or my LVM devices. I assumed this was just a bug with the live CD, so I switched to the Dapper live CD and archived my root file system as I wanted. I then I switched back to the Edgy CD and installed. I wasn't happy to see that the installed version doesn't recognize my RAID or LVM devices either.

What do I need to do to get these drives recognized so I can start getting my system back to normal?

---

### Post by pielgrzym on 2006-11-03
You need to download packages: 'lvm2', and 'lvm-common'. The system might claim that something wasn't installed properly - just ignore it and reboot after installation and lvm should be workim.

IMO it's a HUGE missunderstanding not to put two packages (which take about 488kb of space) neither on live cd nor in normal Edgy system. SHAME and IRRESPONSIBILITY :(

---

### Post by ehird on 2006-11-03
Yes, ubuntu devs should CRY for not including EVERY small package EVER on the CD. CONSPIRACY!!!

---

### Post by pielgrzym on 2006-11-03
Yeah, next time they won't include support for half dozen of file systems. Who needs them anyway... What a windoze way of look :[

Btw. LVM was initially supported by dapper. Did they remove it to make space for another theme or icons? VERY responsible and so innovative....

---

### Post by StratosL on 2006-11-03
I am under the impression that you need the "alternate"  cd (as opposed to "desktop" cd) in order to do soft raid install or upgrades... this detail is  in the directions somewhere...

StratosL

---

### Post by AusIV4 on 2006-11-03
> I am under the impression that you need the "alternate" cd (as opposed to "desktop" cd) in order to do soft raid install or upgrades... this detail is in the directions somewhere...
I was under the impression that the alternate CD was for installing Ubuntu on RAID/LVM. I wanted to install Ubuntu on a hard disk and be able to load a pre-existing logical volume as my home directory, which the Dapper Desktop CD allowed me to do. I wasn't trying to create any volumes, just mount them. Shortly after I installed the necessary packages from the repositories, RAID crashed and my LVM wouldn't load. After several hours wasted, I decided to go back to Dapper and hold out hope that Feisty will work out better.

---

### Post by regeya on 2006-12-30
> **ehird said:**
> Yes, ubuntu devs should CRY for not including EVERY small package EVER on the CD. CONSPIRACY!!!

Charming line.  I'll have to remember it in case the Ubuntu devs ever decide to leave ReiserFS out. ;) 

But seriously, I don't see LVM2 as a small package.  In fact, I find it a little appaling that every discussion I see suggests 'use the alternate install cd if you want lvm'.  My situation today is that I bought a 250GB drive, tried to set up a boot (primary partition) and root (lvm) partition and copied the system over.  Everything copied, should work, but the kernel/initrd combo, despite having lvm stuff built in, sort of freezes with no fanfare during the initrd phase.  Why?  Again, no fanfare.  And all sorts of people more than happy to get me to do a clean install from a different CD.

Well, it's a 3-day weekend, and though there's a local DSL company less than 5 miles away, and despite Verizon offering "naked DSL" here, I live in a no-man's land where the phone cables are about 50 years old and Verizon's in no particular hurry to replace (after all, the lines still work, don't they?) and the only viable option is Hughes Satellite, which is a bit out of my price range.  So to get my hands on the CD, I'd have to drive 20 miles to work...ain't happenin' on a holiday weekend.

All I really need to know is what kernel options I need, what options I need for mkinitramfs, etc. so I can have my root partition managed by lvm, and I'd be very interested to know why such a useful (some might say vital) tool isn't available by default on the standard install CD without some smart butt making sarcastic remarks.

---

