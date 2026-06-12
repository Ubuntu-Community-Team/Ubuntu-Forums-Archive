---
title: "noob q"
date: 2007-11-14
forum: General Help
---

### Post by Spaazkaz on 2007-11-14
I have ubuntu 5.04, I want to upgrade to 7.10. For some reason I cant get the install cd I burned to install in ubuntu... Sometimes it autostarts but when asked to "cancle, unpackage or upgrade" I choose upgrade and errors come up, one of them being 5.04 is no longer supported "please install 6.06..." something along those lines, which brings me back to square one. Is there a way I can override all this during boot? dont know what im talkin about very new to this OS bear with me, ANY help is appreciated, thanks, -ZACK_

---

### Post by rsambuca on 2007-11-14
In order to to upgrade all the way from version 5.04, you would require many steps (ie. 5.04 > 5.10 > 6.06 > 6.10 > 7.04 > 7.10).  It is unlikely that the upgrade in this manner would go very smoothly with that many version changes.  I strongly suggest that you back up your data, and then just do a fresh install of the latest 7.10, Gutsy Gibbon.

---

### Post by ayoli on 2007-11-14
I guess you'd better try a fresh install from the cd, not an upgrade.
Before do that, backup your data.

---

### Post by Spaazkaz on 2007-11-14
I guess my question is how to do a fresh install, my data is backed up. thanks dudes! -Zack-

---

### Post by Spaazkaz on 2007-11-14
i assume i do it right from boot but i want to make sure i dont f it up... this place is great it only take 5 - 10 minutes to solve my problems, freakin awesome. thanks, -Zack-

---

### Post by rsambuca on 2007-11-14
Is your PC set to boot from the cd drive first?

---

### Post by ayoli on 2007-11-14
> **Spaazkaz said:**
> I guess my question is how to do a fresh install, my data is backed up. thanks dudes! -Zack-

you have to boot from the cd (you may need to set that in your bios) not running the cd from your desktop.
then at prompt, choose "start ot install" and go.

---

### Post by ayoli on 2007-11-14
> **rsambuca said:**
> Is your PC set to boot from the cd drive first?

lol, first again, but i'm closer :D

---

### Post by Spaazkaz on 2007-11-14
no, how do i boot from cd... I dont know if it makes a difference but im not dual booting i only have ubuntu.

---

### Post by Therion on 2007-11-14
Well, do you HAVE a CD with Ubuntu 7.10 on it?  If you do, put it in your CD/DVD drive and reboot your computer.  See if rebooting brings up the install menu for Gutsy.  If does, do a fresh install from the menu.

---

### Post by ayoli on 2007-11-14
it's not a matter of dual booting.
At boot, in the very first seconds you have to hit a key (ie: del or F12) to enter in your bios set up.
here you should have the ability to choose the boot sequence (ie: cd first, hdd second, ...)
save and reboot (most of the bios : with F10).

---

### Post by knutschr on 2007-11-14
Insert the CD before starting.
You must restart PC completely.
If you then are not asked to start from CD , restart again and make your changes in BIOS.
(How to login to BIOS varies very much, but at the bottom of screen you will probably (very brief) be told which Fx to tap)

---

### Post by Spaazkaz on 2007-11-14
alright i didn't think it was going to be as straight forward as that. So i got the install menu to come up from both my 6.06 cd and 7.10, but with both cds it says cant read boot, or cant read boot cd, reboot. I clcik ok and it reboots. Am i supposed to have another boot disk, did i burn the iso wrong on BOTH cds? pretty confused.

---

### Post by rsambuca on 2007-11-14
It sounds like you have burned the iso's incorrectly.  [Follow the instructions here]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by Spaazkaz on 2007-11-14
I burned them correctly, if i didn't the  install menu on the cd wouldn't show up right? and i did exactly as that page described... any other opinions?

---

### Post by Spaazkaz on 2007-11-14
THe message is specifically

Error I/O

Cant read boot cd
Reboot


I burned an iso from the website, as it was described on the website, at 4x. I dont think the file is corrupt and i am pissed and frustrated. help me (PLEASE).

---

### Post by Spaazkaz on 2007-11-15
bump

---

### Post by ayoli on 2007-11-15
If your computer can't boot on the CD, that means your cd has not been correctly burn and/or the download was corrupted
to verify integrity of your downloaded file, see here :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
to burn it from any OS, here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Spaazkaz on 2007-11-15
I followed the burn instuctions... and ive downloaded from 3 differnt locations.. and ive burned each of these files at 1x now... my new theory is the cd is only burning the first third of the cd and then stopping and ejecting like it is complete...it seems plausible but i dont know what would be causing this or how to fix it...

---

### Post by knutschr on 2007-11-15
Put your installation CD im burner and [winkey][e], which start your explorer.
Open CD. You should see 11 maps, an icon, autorun.inf among some others.

If not, you could try another free and very good win burner
[http://cdburnerxp.se/](http://cdburnerxp.se/)

---

### Post by Spaazkaz on 2007-11-15
I dont have windows though, only ubuntu, thanks though

---

### Post by rsambuca on 2007-11-15
You never answered the question:  Did you check the md5sum prior to burning the iso?

---

