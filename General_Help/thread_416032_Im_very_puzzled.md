---
title: "Im very puzzled"
date: 2007-04-20
forum: General Help
---

### Post by Lax101 on 2007-04-20
Well just to give a background on the machine i have.

AMD X2 3800+
2GIGS OF OZC PC3200
300 GIG
EVGA 8800 GTS 640
750 PSU

Well I installed wondows with no problem.  So i decided to install ubuntu 7.04 i created the cd and went to install and what happens it starts to load the kernel and the you know starts to show the ubuntu splash screen and just sits there and does nothing.  So i then decided to try ubuntu 6.10 and it does the same thing except it shows a black screen with a blinking cursor.  So im puzzeled so im now downloading the 64 bit version to see if it was the vesrions was wrong.  Does anyone have a clue to what my problem might be?:confused:

---

### Post by kornhead127 on 2007-04-20
You should be ok with the 64bit edition. If I'm not mistaken the AMD X2 is a 64 bit processor.

---

### Post by jiminycricket on 2007-04-20
can you press CTRL + ALT + F8 or CTRL + ALT + F1 to see where the bootup is stopping?

---

### Post by kornhead127 on 2007-04-20
I think pressing [esc] will show the messages. But I'm not sure.

---

### Post by Lax101 on 2007-04-20
ok so i tried the 64 bit version.  Im getting closer so i found out what the rror was but  really have no clue what the error indicates.
[       94.075928] Buffer I/O error on device fd0, logical block 0

so thats the error i get and thats all it gives me even after a restart and even if i go into safe mode on the disk.  So after i got that error on both i ran a check disk for errors and it came up clean so im pretty clueless right now. Any other ideas

---

### Post by jiminycricket on 2007-04-20
Could be this bug: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306) 

Have you also tried booting with acpi turned off (just as a general solution to problems)

---

### Post by orb9220 on 2007-04-20
> [ 94.075928] Buffer I/O error on device fd0, logical block 0

I believe is the floppy drive.

---

### Post by srt4play on 2007-04-20
I had this error and poster above me is right fd0 refers to the floppy drive. I didn't actually have one in my machine so I disabled the floppy controller in the bios and Ubuntu booted right up no problem.

---

### Post by Lax101 on 2007-04-21
yeah someone i forgot who it was sent me a link for the same issue which I resolved.  Now however im having a video card issue.  It works however its not using the proper drivers and i for got how to install the nvidia drivers for the 8800 series card.  I'm hoping they have made some cause i tried fixing it the first time and messed up the system.  Does anyone have any suggestions or could help me it would be greatly appreciated.

---

