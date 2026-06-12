---
title: "How can I run Ubuntu in Windows"
date: 2007-12-31
forum: General Help
---

### Post by Swaad on 2007-12-31
I know that it possible to run ubuntu inside a window in my windows XP Media Center edition installation. I want to know how i can do this and will this efffect the mbr in any way. Also I've been getting errors ever since i uninstalled ubuntu from my system and put Vista on it the errors are Blue Screens. After that i uninstalled Vista and put XP media Center on it but I am still getting serious errors is this because of the mbr has been written with bad data which causes the system to fail on the drivers. How can I do what i am trying to do please email [email]swaad@therobotmasters.com[/email] of all your answers that are solid.

---

### Post by ~LoKe on 2007-12-31
[https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

---

### Post by logos34 on 2007-12-31
yeah, Wubi or the VMWare Server route.

---

### Post by Swaad on 2008-01-01
No, I dont want the GRUB interface to show up when I boot because that screws with MBR and I dont want that. What I want is for example I am posting this in an Internet Explorer window I want to run Ubuntu in a Window like that. Also when i got rid of Ubuntu and GRUB what happened was the partition Ubuntu was on is now free and i do not know how I can put this partition back with the main HD. Please tell me how I can put unallocated partition back into the main HD without 3rd party software.

---

### Post by dward526 on 2008-01-01
To run Ubuntu in a window, you need to use virtualization software.  Some good ones are VMWare and VirtualBox (My favorite).

To add the partition back to windows, you probably need to use third party software.  I cannot remember if Disk Management in XP can do this, check it first though to see.  You can also just format the partition to NTFS in Disk Management and use it a data partition , for example.

---

### Post by Swaad on 2008-01-01
OK I understand a little more about the virtualization software. What I want to know now is will it mess wih my MBR or hardware? Also what freeware 3rd party software can I use to solve my problem without uninstalling or damaging Windows. I currrently user XP Media Center Edition.

---

### Post by bigken on 2008-01-01
[virtual pc]("http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx") will do this for you without affecting you mbr

---

### Post by bigken on 2008-01-01
the blue screen (BSOD) if you could tell us what the error report says ie look for ati or nvidia would mean a bad video driver but this could be any number of things such as a failing hdd bad ram ect

---

### Post by Swaad on 2008-01-01
> **bigken said:**
> [virtual pc]("http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx") will do this for you without affecting you mbr
Bigken if I were to download this Microsoft Product how would it work. How would i be able to allow it to corresspond to Linux. I know I'm sounding kinda n00bish but I dont wanna have a problem like I did before. Also what if I dont like the Virtual PC anymore do I just simply uninstall like anything else. Also what about my partition problem.

---

### Post by bigken on 2008-01-01
just install it in windows make your virtual pc for linux its that easy if you dont like 
uninstall it delete your virtual pc's 1st :)

---

### Post by Swaad on 2008-01-01
> **bigken said:**
> the blue screen (BSOD) if you could tell us what the error report says ie look for ati or nvidia would mean a bad video driver but this could be any number of things such as a failing hdd bad ram ect
For the blue screen umm in Vista I was getting errors cause of my video card. I think the Blue Screen stopped since I downgraded to XP. Please do help with the partition error though.

---

### Post by bigken on 2008-01-01
to fix your mbr boot from the windows xp cd 
go to repair console 

at the prompt type 

fixmbr 


fixboot 

exit 

answer yes to all

---

### Post by Swaad on 2008-01-01
> **bigken said:**
> to fix your mbr boot from the windows xp cd 
go to repair console 

at the prompt type 

fixmbr 


fixboot 

exit 

answer yes to all
I just wanna know how I can put back the free space to my main hard drive.

---

### Post by bigken on 2008-01-01
use gparted live cd it works a treat delete the free space and enlarge your partiton

---

### Post by Swaad on 2008-01-01
Can we stick to a Windows tool? I dont want to go anywhere near gParted.

---

### Post by bigken on 2008-01-01
I dont know of any windows tools in my experience gparted is doggies bolocks

---

### Post by ~LoKe on 2008-01-01
Uh...to be honest...perhaps you shouldn't be on a linux forum right now?  You're asking about using Windows only tools, to install something in windows.  Ubuntu is only a small part of what you're after.

---

### Post by aysiu on 2008-01-01
Use VirtualBox. This link will walk you through the *entire* process with screenshots:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

And, no, it won't affect the MBR, and it does not require you to repartition.

---

