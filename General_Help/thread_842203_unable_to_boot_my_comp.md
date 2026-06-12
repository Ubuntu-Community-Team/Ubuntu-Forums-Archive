---
title: "unable to boot my comp"
date: 2008-06-27
forum: General Help
---

### Post by joyson20 on 2008-06-27
i was trying to reload the synaptic manager....i clicked on the reload icon...but it got stuck and nothing was happening....so i restarted my comp....when i restarted my comp it was not booting...please help or atleast tell what i should do..thanks

---

### Post by enchesss on 2008-06-27
at what stage does it lock up?
do you get a post message from your bios?

---

### Post by joyson20 on 2008-06-27
no nothing...the cpu turns on but the monitor does not show any thing..but it is on

---

### Post by enchesss on 2008-06-27
if you are sure that the computer turned off before you restarted it then it sounds like a hardware problem.
the most likely cause in this situation would be that there was a problem with updating grub or your video drivers but you should get a post bios message AT LEAST.
It therefore sounds like a RAM problem but it could be mobo or video card too.

Does the computer make any sounds (beeps)?

if so then try booting with a live cd

---

### Post by joyson20 on 2008-06-27
it does not make any beep sounds.....i tried with the live cd also...it too is not working

---

### Post by joyson20 on 2008-06-27
the comp didnt turn off...it got stuck in the reloading window..so i forced it to restart by pressin the restart button in the cpu

---

### Post by enchesss on 2008-06-27
if the computer is not making a beep then the bios is not working.
this most probably means that there is a problem with your mother board.
how old is the mother board?
do you know what brand it is?

you say that the cpu is on - how can you tell?

---

### Post by joyson20 on 2008-06-27
it is 18 months old....its from HCL....

I thought that my cpu was on because the light is on...

---

### Post by enchesss on 2008-06-27
ok
sorry - from what you say it must be a problem with you mother board.
the light you see just means that the hard drive is getting electricity -
can you describe what the light does?
Does it turn off when you shutdown the computer?
Try completely shutting down, taking the power cord out of the back (carefully).
Then turn it back on again and also - does that fan inside the computer work?
Is your computer in a dusty place?

---

### Post by WRDN on 2008-06-27
Did you ever make changes to your BIOS?

As enchesss said, the BIOS is not working properly, so the PC will not post.
You could try resetting the CMOS- have a look in the motherboard manual, or on the board itself. There should be a little jumper that can be removed. If and when you find it, take it off, and put it back on. This should reset the CMOS, and in turn, the BIOS.

---

### Post by joyson20 on 2008-06-28
hey guys thanks a lot for your advice....it was some problem with the motherboard...all i did was this..i inserted my motherboard installation cd in the drive and restarted my comp....it worked perfectly....i must Thank God....Now back to ubuntu and enjoying it....thanks again for ur quick and effective help....

---

### Post by cainram on 2008-07-08
I had a similar problem but it was obviously caused by a different problem.
I booted my computer and experienced a problem I've had before: it seems that sometimes the drivers don't load properly (or something...) and I can't get past 640X480 resolution. Restarting usually fixes the problem but this time when I rebooted nothing happened. I got the usual mobo beep but it hung at the bios splash screen and wouldn't load GRUB; I couldn't even get into the bios (so, obviously, I couldn't even boot from a cd...). Anyway, a friend recommended that I reset the CMOS by either unplugging the computer and removing the battery for a minute or simply looking for a cmos reset jumper. The jumper area has three pins, two of which are jumped by default. I removed the power cord and took the jumper off of pins one and two and jumped pins two and three. After replacing the jumper to pins one and two the computer booted and all was fine. Ubuntu runs a sort of disk integrity check (I think...) and it's all good. Remember, though that this resets your bios settings and you may have to remind the mobo if you don't have a floppy drive, etc... I know this was a rambling post and that the user and I didn't have the same problem but I looked in this thread for help for my problem so others may do the same.

---

