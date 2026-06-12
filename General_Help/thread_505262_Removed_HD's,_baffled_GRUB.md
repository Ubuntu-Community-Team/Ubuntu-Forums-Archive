---
title: "Removed HD's, baffled GRUB"
date: 2007-07-20
forum: General Help
---

### Post by JusticeZero on 2007-07-20
I had my computer running Ubuntu with a dual boot to XP, on seperate drives. Primary Master=Windows, Primary Slave=ubuntu, secondary master=CD-ROM.
The Ubuntu drive was small and slow though, and I needed to deal with some files and such, so I got a new 160GB drive and installed it as Secondary Slave, so I could copy files over; I installed Ubuntu on that drive as well.
(computer at this point is 1M WinXP, 1s ubuntu, 2M CD-ROM, 2s Ubuntu).
The power supply was small, the computer tech said "It should have enough power, but keep an eye on it just in case." It was very cold, so in my room I bundled up in a sweater and jacket. It worked perfectly, I transferred my files and everything.
Then today, it warmed up. I found I only needed a T-shirt to boot up my computer, which promptly overheated and shut down.
So, I did this:
Removed 1M and 1s (Windows and small ubuntu). Connected 2s (big shiny new Ubuntu) to primary master.
Tried booting up. it hung.
Loaded in my boot CD. Went through various tutorials to get GRUB back (in hda2, the / partition - I have hda1 swap, hda2 /, hda3 /home, and if I should be setting those up differently please tell me). 

Now when I boot up, I get my nice familiar GRUB window back, the one that wants to boot Ubuntu off of one of the slave drives (which I no longer have) or Windows on primary master (it's Ubuntu now) and won't boot anything.
I'm now on the boot CD, and my skills have run out. I can't seem to figure how to get GRUB to realize that it's list of drives is wrong, let alone while working through the CD.

---

### Post by mikewhatever on 2007-07-20
> Now when I boot up, I get my nice familiar GRUB window back, the one that wants to boot Ubuntu off of one of the slave drives (which I no longer have) or Windows on primary master (it's Ubuntu now) and won't boot anything.
I'm now on the boot CD, and my skills have run out. I can't seem to figure how to get GRUB to realize that it's list of drives is wrong, let alone while working through the CD.
Highlight the entry for Ubuntu and press e. Edit the (hdx,y) part end try to boot. If it works, you'd have to edit the menu.lst to make the change permanent.
> gksudo gedit /boot/grub/menu.lst

---

