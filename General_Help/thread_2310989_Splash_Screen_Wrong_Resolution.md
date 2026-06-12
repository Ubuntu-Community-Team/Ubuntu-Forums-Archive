---
title: "Splash Screen Wrong Resolution"
date: 2016-01-23
forum: General Help
---

### Post by typos1 on 2016-01-23
I got a new pc a few months back, all is running fine, but theres a problem with the splash screen that is annoying, - its the wrong resolution and when it first starts it goes all funny and all I can see are 4 large purple dots. 

Its not causing any problems, but for aesthetics I d like to sort it out, I remember having a similar problem on my old pc and I had to do something like "nomodeset" to correct it, but that had Nvidia graphics, my new one has Radeon graphics.

Ca anyone tell me how to sort it our for Radeon graphics ?

---

### Post by Petro Dawg on 2016-01-23
Thank you for inspiring me to fix a similar issue on my PC.  After installing Nvidia drivers the splash screen always looks like trash.  I borrowed/stole from a solution posted [here]("http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen").

This was my fix...

I couldn't get the "hwinfo" from the original solution as it doesn't appear to be available for me in the current repos.  I did install "v86d", but I don't think it actually helped with anything.

So I ran..
```
sudo gedit /etc/default/grub
```

Below the "GRUB_GFXMODE=" entry I added..
```
GRUB_GFXPAYLOAD_LINUX=1024x768
```
 You may have to play around with the resolutions.  I tried several but only 1024x768 worked for me. 

I then saved the grub file and ran the following...
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub
sudo update-initramfs -u
```

Rebooted and presto-chango I had the original splash screen back again.  This doesn't appear to be graphics card specific so it may work for you as well.

---

### Post by typos1 on 2016-01-23
Great, thanks !

Just tried it and it didnt make any difference :-( (I put a # before "GRUB_GFXPAYLOAD_LINUX=1024x768" though.)

---

### Post by Petro Dawg on 2016-01-23
Do not use a #, that signals a comment line.  You want grub to actually read and use the line. 

Be sure to run the following after fixing the grub file...

```
sudo update-grub
sudo update-initramfs -u
```

---

### Post by typos1 on 2016-01-23
Doh !

Tried it without the #, but start up is exactly the same as before but with some command line briefly flashing up saying "no hardware found" and something else which I didnt catch cos it was too fast.

I also tried just changing the resolution of the entry "GRUB_GFXMODE=" which on my machine was 640x480 originally, but it made no difference.

---

### Post by Petro Dawg on 2016-01-23
Did you try to set resolution for GRUB_GFXPAYLOAD_LINUX other than 1024x768?  That happens to work on my system, but it may not on yours.  Be sure to run those update commands every time you change the grub file.

I would also put that # back in front of "GRUB_GFXMODE=" line

---

### Post by Petro Dawg on 2016-01-31
I also recently found which resolutions GRUB can use by accessing GRUB (hold down shift during boot), pressing "C" for command line, and typing: VBEINFO 

Make sure you use one of the listed resolutions or the proper splash screen will not appear.

---

### Post by typos1 on 2016-06-16
I ve had this thread open in my browser for months, have meant to get around to trying more to get this right, but recently the problem seems to have cured itself ! Maybe an update corrected it or something ?

---

