---
title: "AMD64 Boot error (blankscreen)"
date: 2008-04-08
forum: General Help
---

### Post by matt_UK on 2008-04-08
I've tried to use the new wubi off the beta iso of ubuntu hardy heron and i'm having no luck. For some reason after installed the amd64 version on my pc and selected the ubuntu option off the boot menu, The screen just goes blank.

I think its a grub error of some sort. I get this text when i press insert i get this

```

hard drives 1, int 13:F0006FF0, int 15: F000E859
get_diskinfo(80), int 13/41(80) ,version AA210005, int 13/48(80) err=0, C/H/S=0/
0/0, Sector Count/Size625142400/0, int 13/08(80) 
```

I have a 320 gig hard drive and an amd x2 athlon.

Any ideas? :P

PS The 32 bit version works on my older pc.

---

### Post by ago on 2008-04-08
press esc at boot and select the second option

---

### Post by matt_UK on 2008-04-12
nope i still have the same problem, its as if It hasn't even installed the files.

---

### Post by ago on 2008-04-12
The files are installed after the first reboot, the windows side of things only makes the installation files available without actually installing them

Do you have any other error to report? Have you check that your video card is compatible by using the live CD? A quick googling for your make and model should also provide some indication.

---

### Post by matt_UK on 2008-04-13
[QUOTE=ago;4702867The files are installed after the first reboot, the windows side of things only makes the installation files available without actually installing them
[/QUOTE]

Thats what I mean't the installation files. Literally nothing will show up,the only thing onscreen is a flashing   _    in the top left of the screen.

---

### Post by ago on 2008-04-13
Do you see some booting messages scrollbars before that?
When you press esc after "Ubuntu" at reboot did you try the other options? In particular "Safe video mode" or "Rescue Mode".

---

### Post by matt_UK on 2008-04-13
like i said nothing will show up it'll just skip to the flashing _.

I think i might need to download a new iso once hardys out of beta,

thnx for your help anyways.:guitar:

---

### Post by valant on 2008-04-26
I am unfortunately encountering this same exact error. After picking Ubuntu in the bootloader, it just goes to a completely black screen when a blinking _ in the top left corner. No key (including escape) seems to do anything, and I'm forced to reboot via hardware. AMD64 3000+ Venice Core, 1GB RAM, 25GB free disk space. Suggestions would be wonderful.

P.S. Forgot to mention this is using Wubi 8.04 trying to install the final release of the Hardy Heron 8.04 amd64 iso (they are of course both in the same folder, I also tried mounting the iso and installing it via Wubi on the image, but it resulted in the same error). 

P.P.S. Sorry, forgot another useful bit of info. This is on Windows XP Professional SP2.

P.P.P.S. Man I really suck at this posting thing -- My Video Card is an AGP ATI X800 Platinum Edition. I tried googling for compatibility but couldn't find anything conclusive.

---

### Post by ago on 2008-04-26
Press esc at boot after "Ubuntu" and try the other boot options

---

### Post by valant on 2008-05-13
That doesn't work, I have the same problem as the original poster. After pressing Enter on Ubuntu, it goes directly to a black screen with a blinking _ in the top left. Nothing from my keyboard evokes a response at this point (by accident, I left NumLock on one time before entering this screen, and I couldn't even turn that off). Pressing Escape beforehand just brings up the Windows boot options and doing so afterward doesn't do anything (have to hard reboot).

I tried installing the i386 version today with the same results. At this point I'm thinking it might be my video card (I don't have integrated graphics on my mobo so I can't test)? Although this problem seems to crop up among only amd64 users (from what I've seen) so I don't know.

If anyone else could provide insight I'd be grateful, I'd really love to get Ubuntu up and running.

---

### Post by ago on 2008-05-14
> **valant said:**
> After pressing Enter on Ubuntu, it goes directly to a black screen with a blinking _ in the top left.

Hmm, after you press Enter on Ubuntu at boot you should see a countdown 5, 4, 3, 2, 1... With a message like "Press ESC for more boot options..."

If you see no countdown then try to press "insert" immediately after selecting ubuntu

---

