---
title: "Hang-Up During Shut Down Process"
date: 2007-07-17
forum: General Help
---

### Post by kmano8 on 2007-07-17
I installed 7.04 last night and did all the necessary updates.  I updated the nVidia drivers as well and installed some audio/video codecs.  I was able to restart my PC with no problem.  When I was done for the night, I shut down ubuntu and left the room.  When I came back in the morning, I noticed that my computer was still on.  It was hung up at the progress bar screen (the progress bar was completely empty -- all black).  I did a hard shut off and rebooted to try again, but encountered the same problem.  Any idea as to why this is hanging?

Intel P4 3.0ghz HT and an nVidia 7600gt.

Thanks!

-Karl

---

### Post by rscott5 on 2007-07-17
What type of computer is it? I bought a new Dell XPS 410 a couple weeks ago and apparently that model has a known problem with the kernel when rebooting, but not when shutting down. The solution I found was to pass "reboot=b" to the kernel at boot time. That prolly won't work for you if you don't have either a Dimension E520 or an XPS 410 but it's worth a shot. Heres the link for my related post: [http://ubuntuforums.org/showthread.php?t=493010](http://ubuntuforums.org/showthread.php?t=493010) And the Dell support link is here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Hang_on_reboot)

If it is a problem with the kernel like mine, but that doesn't solve it then I guess just use shutdown for now until they update the kernel again (which is every 2-3 months I believe?).

You might try posting some more system specs like motherboard, bios version, etc. and someone may be able to help more.

---

### Post by kmano8 on 2007-07-17
I have a self-built system:

Motherboard: ASUS P5GDC Deluxe LGA 775 Intel 915P
Processor: Intel Pentium 4 530J Prescott 3.0GHz LGA 775 Processor Model BX80547PG3000EJ
RAM: CORSAIR XMS 1GB (2 x 512MB) 184-Pin DDR SDRAM DDR 400
Graphics: XFX PV-T73G-UDD3 GeForce 7600GT 256MB GDDR3

I'll try your suggestion.. thanks.

---

### Post by kmano8 on 2007-07-18
Again, this is a fresh install... since that, I've added beryl, some codecs, muted a sound input, and did all requested updates.

---

### Post by kmano8 on 2007-07-18
anyone?

---

### Post by rbmorse on 2007-07-18
No specific idea, but I know of other 915-chipset boards that exhibit the same behavior. 

Did the reboot=b trick work? 

RBM

---

