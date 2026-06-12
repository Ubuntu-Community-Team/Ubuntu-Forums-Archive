---
title: "live cd problem... please advice"
date: 2005-03-20
forum: General Help
---

### Post by Alecsu on 2005-03-20
I have i little problem... i've got a live Ubuntu cd (warty), i place it in the cd-rom and reboot the computer...it is showing the boot optios on the screen appears a logo of Ubuntu in a light brown picture and a progress bar underneath...ok...but after the progress bar fills up THE COMPUTER RESTARTS and start the boot sequence once again...

What seems to be the problem? Is there a specific option that i should choose in the beginning? Is my live cd corrupted? 

Please help...


P.S. please forgive my poor english...

---

### Post by vignesh on 2005-03-20
WHEN I PUT THE CDROM.I GET A BLANK SCREEN .I EVEN INSTALLED UBUNTU BUT MY MONITOR SEEMS TO BE NOT CONFIGURED.IN KNOPPIX I GOT AN ERROR SAYING 
"SYNC OUT OF RANGE" THEN WHEN I GAVE THE BOOT COMMAND AS 
knoppix  xvrefresh=50 THE LINUX DESKTOP COMES.WHAT IS THE PROBLEM HOW DO I
SOLVE THIS PROBLEM IN UBUNTU LIVE CD.
THANKS IN ADVANCE

---

### Post by dewey on 2005-03-20
If you downloaded the iso yourself, try comparing the md5 checksum, to ensure there were no errors during the download.  And try burning the cd at a maximum of 16x, it's hard to believe how many of these errors can be traced back to bad burns or corrupted isos.

---

### Post by vignesh on 2005-03-20
I actually  got a cd from the Ubuntu shipit.

---

### Post by Alecsu on 2005-03-21
i tried the cd in another computer... works just fine... i think Ubuntu does not like my GeForce FX5200  :( ... too bad, i think i'll return to Knoppix...

---

### Post by dewey on 2005-03-21
I haven't heard of nvidia problems with the live cd... it's much easier to use nvidia drivers than it is with ATI.

Try messing with the bootup options?

---

### Post by Alecsu on 2005-03-22
yas, i tried them...i've tried my disk on three different pc's and worked ....mepis or knoppix  don't seem to have a problem with my hardware...FX5200, 2x40gb WD, 512 ddram, MB-nforce2 ...
i really wanna try ubuntu... :(

---

### Post by unisol on 2005-04-06
[QUOTE=Alecsu]i tried the cd in another computer... works just fine... i think Ubuntu does not like my GeForce FX5200  :( ... too bad, i think i'll return to Knoppix...[/QUOTE]
 sometimes the chipset in thse motherboard is incompatible with the live cd

---

### Post by vignesh on 2005-04-06
IN knoppix I have to give the boot option as knoppix xvrefresh=50 or hsync=50 onlt then it works.So what do I have to do in Ubuntu.I have a nvidia geforce 2.

PS: Sorry for the late reply I had exams so was unable to visit the forum.I love ubuntu a lot and really want to see it on my comp.please help me.

---

### Post by vignesh on 2005-04-07
Please can someone reply soon.

---

### Post by vignesh on 2005-04-08
it worked at last I had to give two boot parameters xmodule=nv and hsync=50
thanks to all

---

