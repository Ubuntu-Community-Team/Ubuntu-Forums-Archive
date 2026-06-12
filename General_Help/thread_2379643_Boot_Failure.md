---
title: "Boot Failure"
date: 2017-12-07
forum: General Help
---

### Post by hans12345 on 2017-12-07
I have a catastrophic boot error.
The system has been working normally and to my knowledge there have been no recent changes. There was a sudden power cut a few days ago but the system seemed OK after that.

What happens, 4 different cases:

1. Normal boot
--------------
- I boot up
- I get the grub screen, everything is OK
- whatever I do (eg boot normally, boot into recovery, or nothing at all) after about 15 seconds the PC crashes

The crash looks like a graphics problem: the screen flickers and lines of dots flash across the whole screen. These keep changing as if the PC is working properly.  I think it is called screen tearing. After about 20 seconds, there is a change in the display. There is the same flicking pattern but with more colour.
(I could imagine that now the boot process is complete and the PC is now showing the normal home screen. But it may simply have crashed)

2. Boot from Ubuntu CD
----------------------
- Screen stays black
- CD light flickers on and off (reading from CD) for about 2 minutes
- Then nothing. Screen black.

3. Boot from old Hirens Boot CD
-------------------------------
- boots OK
- start Memtest86
- this runs normally for 5 mins 45 secs then freezes. Screen visible and stable, still on pass 0, no errors found

Reran the Memtest86. I think it crashed after 4 mins 21 secs, but could not be certain since the image broke up and started flickering, but different style of flickering than I saw in case 1 above. This looks more like the symbol table is corrupted.

4. Boot from old SystemRescue CD
--------------------------------
- boots OK
- at menu list, STARTX chosen. Screen goes funny, then black, but after 30 secs the screen recovers and the GUI appears with the Terminal in a box in the centre.
- In var/log I can access messages and xorg.0.log but these only show the SystemRescueCD boot. No obvious errors.
- system seems stable 

I can of course boot into the BIOS UEFI with no problem.

My question is where and how do I track down the cause.

I could try to look for log files using something like Hiren/SystemRescue. If I can look around on the drive, where should I look and for which files?

Is this a problem related to:
- the graphics card or driver? (I think not, after all it starts OK and crashes after a short time regardless of what I do, Except with SystemRescue)
- memory?
- CPU / motherboard failure ?
- power supply ?
- X / XORG ?
- corrupted HD ?

Details of the system
Hardware:
- home built PC, updated about 2 months ago, been working well until now
- recent CPU (Intel Pentium G4560)
- recent Prime B250M-A M/B 
- recent Crucial memory (8GB DDR4)
Software : Ubuntu 16.04 LTS fully updated

I know this is a confusing post, but I really appreciate some guidance.

---

### Post by hans12345 on 2017-12-08
More results, and some clues.

I started again early today, and found the  SystemRescueCD did not work -  more flickering /  screen tearing.
Then I went to the BIOS - also crashed - more flickering /  screen tearing

I left it running for an hour, I was busy elsewhere.

I rebooted into the BIOS, seemed OK. One more hour,  I was still busy elsewhere.

Tried a normal boot - now it boots into Ubuntu !

So, this appears to me to be a temperature related problem?

---

### Post by leunam12 on 2017-12-08
If you suspect that it is overheating, then you have to remove the dust from the cooling system; overheating will kill your computer. If it is a desktop PC it is very easy, just remove the side panel and use compressed air to blow the dust out, make sure that you clean the CPU's heatsink very well. If it is a laptop what I usually do is remove the keyboard, this will expose the fan (or at least partially), and then blow compressed air from the exhaust vent into the computer and all the dust comes out from the fan. then I do it in the opposite direction blowing into the fan and let the air come out from the exhaust vent.

---

### Post by leunam12 on 2017-12-08
Seems like a hardware issue. If you cannot boot from CD it is very unlikely that the problem is the Hard Drive. 
Drain the power from the motherboard entirely by unplugging the PC and holding the power button for at least 
30 seconds, then try booting with one stick of RAM only, if it doesn't work use the other one. Try different slots. 
If you have access to another power supply, try that. 
What kind of video card do you have?

---

### Post by hans12345 on 2017-12-08
> **leunam12 said:**
> Seems like a hardware issue. If you cannot boot from CD it is very unlikely that the problem is the Hard Drive. 
Drain the power from the motherboard entirely by unplugging the PC and holding the power button for at least 
30 seconds, then try booting with one stick of RAM only, if it doesn't work use the other one. Try different slots. 
If you have access to another power supply, try that. 
What kind of video card do you have?

Thanks for your posts.

I am now thinking towards a hardware problem.

On your first post, if it is a temperature problem it would mean that when the PC is cold I have the problem. After it warms up after a hour or two the problem disappears (or it has once so far).

I'll try the warm up technique again and try memtest to check the memory.

I did not mention a video card because I am using Intel's integrated graphics.

---

