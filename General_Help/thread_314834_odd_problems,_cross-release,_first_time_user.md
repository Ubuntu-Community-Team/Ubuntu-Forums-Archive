---
title: "odd problems, cross-release, first time user"
date: 2006-12-08
forum: General Help
---

### Post by ABentSpoon on 2006-12-08
While trying to install from a live cd, the cd will come to a burnt orange screen, and freeze there. Minor graphical glitches could also be seen on the initial boot screen (boot live/install oem/check for errors on disk screen)

I then downloaded and burnt 6.06, but had the same problems, however, I was able to install as OEM.

After the installation, it would just get to the login prompt, and freeze there. I only have a spilt second of functionality before it freezes after it hits the login page. I've been playing with settings in dpkg-reconfigure (i have tried versa) but there are graphical glitches in there also (the left side of objects seem to freeze. half of the scrollbars, the first letter in the list of video drivers, and the cursor is always one space away from the end of hte text.

Does anyone have any idea what could be causing this? It's my first linux installation, and i'm rather confused.

---

### Post by ABentSpoon on 2006-12-08
forgot to mention i'm running a gateway, with an intel celeron and an 80810 integrated graphics card


..yea okay so it's a bump..

---

### Post by wpshooter on 2006-12-08
Let me see if I understand you correctly.

You are trying to install from the DESKTOP (sometimes referred to as live CD) and also ARE you checking the integrity of the CD by running the verification function as found on the initial Ubuntu boot screen menu ?

How much memory do you have ?

---

### Post by ABentSpoon on 2006-12-08
I've got 386 meg of ram.

As for how i'm trying to install it, it was locking up while loading the desktop to install from the desktop, however, i was able to use the OEM install to successfully install ubuntu.

When i boot from my installation, i get a similar problem, it locks up as soon as i get to the login screen.

I assumed it had somthing to do with the video card, as I had other glitches mentioned above that seemed very graphics related. I've tried several different options in the dpkg-reconfigure menu, including using versa (i belive that's what it was called) but none of the settings got me any further (or even as far as i got actually)

---

### Post by wpshooter on 2006-12-08
Are you burning your CDs at  4X or slower ?

Again, are you checking the integrity of the CD by running the verification function found on the initial Ubuntu boot screen menu ?

Have you tried installing using the video safe mode ?

If any of that does not help, you may want to installing using the ALTERNATE CD.

Also, are you running any other O/S on the machine or is this to be strictly a Ubuntu machine ?

---

### Post by ABentSpoon on 2006-12-08
Yes, I burnt the cd's at 4x, and I did run the verify tool.

I used the cd for edgy, and the dvd version for 6.06, and both hung up at the same point. I didn't attempt to install using the save vga mode, as I got it to install using the OEM installation.

---

### Post by ABentSpoon on 2006-12-08
Oh, and, I'm dual booting with XP, but that's on a different hard drive.

---

### Post by wpshooter on 2006-12-08
I don't understand exactly why you are installing as the OEM.

But here are my recommendations, assuming that you have no other O/S or data on the computer that you need to keep.

Download and burn the ALTERNATE version (text based install) of the CD.

Download the **KILLDISK** program and **WIPE** your drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then install from your ALTERNATE CD version.  Pay close attention to the video parameter choices that come up during the text install.

I think this may take care the majority, if not all, of your video problems.  And if not, come back and I or someone else can tell you how to properly fix.

Good luck.

---

