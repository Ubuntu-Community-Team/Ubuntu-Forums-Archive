---
title: "I need help with using the Live CD"
date: 2004-12-01
forum: General Help
---

### Post by thunderstruck on 2004-12-01
I am not able to load the Live CD. I put it in the drive and restart my computer, but then it still loads Windows XP. Can somebody please help me because I am very interested in using Ubuntu. Thanks.

---

### Post by zenwhen on 2004-12-01
Can you get into your bios? 

If so, then just find your boot priority settings and highlight your CDrom drive and hit "+" till its at the top. Save changes and reboot.

---

### Post by BWF89 on 2004-12-01
[QUOTE=thunderstruck]I am not able to load the Live CD. I put it in the drive and restart my computer, but then it still loads Windows XP. Can somebody please help me because I am very interested in using Ubuntu. Thanks.[/QUOTE]
I had the same prolbem with my SuSE GNOME live CD. All my other live CD's work fine  but for somereason it just want back to windows when I restarted. And now it's sitting somewhere in Valley Landfill...

---

### Post by adbak on 2004-12-02
I know that on Dell computers, at least, they have a button that you push as the BIOS is loading.  F12 allows you to tell the computer which place to load first -- whether you want a normal boot-up, floppy drive, cd-rom, etc.  I forget what the options are, but you're able to tell it to boot from the cd drive.  This action only works once instead of each time like it would if you messed with your BIOS.

Right after you turn the power on to your computer, take a look at the first screen and see if it lists any buttons for System Setup or any Boot Options or otherwise described.  That's all I can tell you how to do, as each computer is different.

Try searching Google to find the instructions for your particular computers.

---

### Post by gecko13 on 2005-11-12
If your SUSE live (DVD) is working then set your bios boot settings to the following;
DVD (sounds like this works already)
CDROM 
FLOPPY
HARD DRIVE
these bios settings will not hurt anything and it will allow your computer to look at all your non-standard drives first.
usually F1 or DEL gets you into bios.

---

### Post by teaker1s on 2005-11-12
configure bios to boot floppy/cdrom/dvd and then harddisk and if that still doesn't work then disable search for other boot devices
while we're talking about live boot anyone care to explain how to mount primary master hd as I killed xserver and knowing how to access harddisk through live cd would make it easy to fix in a gui way as I'm not fond of too much comand line or nano. 

thanks

---

