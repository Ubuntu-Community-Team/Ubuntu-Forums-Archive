---
title: "[SOLVED] Power Outage"
date: 2007-09-07
forum: General Help
---

### Post by DougieFresh4U on 2007-09-07
About 2 hours ago a transformer in my area caught fire and all power went out. I have all 4 of my machines hooked to power strips.
When the power came back on and I booted up this machine, I was presented with a black bar across the screen. I tried 2 other monitors and both had the black strip across, so I know it's not the monitor. 
Any one have and idea whats wrong? Do I need to redo X? 
Thanks
EDIT: Seems that I can not get screen shot of it, but believe me, it's a fat wide black strip across my screen. Can;t see whats under it so I have to scroll up & down to see where I'm at to type & read

---

### Post by EndPerform on 2007-09-07
Are all of these machines hooked up to the same monitor?  If so, it's possible it could be the monitor itself, or else it might be a hardware-related issue.  If you have another OS on one of the machines with this problem, try rebooting to the other OS and see if it persists.

---

### Post by DougieFresh4U on 2007-09-07
> **EndPerform said:**
> Are all of these machines hooked up to the same monitor?  If so, it's possible it could be the monitor itself, or else it might be a hardware-related issue.  If you have another OS on one of the machines with this problem, try rebooting to the other OS and see if it persists.

Thanks for reply. As stated in first post, I tried 2 other monitors on this machine and black bar is present. Other machines, the monitors work ok. This machine has an onboard video card. I have an ATI card lying around here some where. Could it be the video card? Suggestions please!!

---

### Post by tgalati4 on 2007-09-07
Sometimes you will get black bars if you are not getting 60 Hz AC power.  Also, you might need to reset the video cards by unplugging the computers for several minutes and then booting normally.  Try setting the video refresh rate to 60 Hz first then march the values up to what they were previously.

Of course, they could be damaged.

---

### Post by DougieFresh4U on 2007-09-07
Thanks for replies:)
It's the Intel i810 video card. I tried suggestions and black bar is still present
I have an ATI card laying around here. Would it be alot of hassle to just put it in slot and fire up machine? How about a reinstall? would that maybe solve my problem.

---

### Post by DougieFresh4U on 2007-09-07
Ok, this is what I have just tried:
the problem is with my Gutsy machine. I put in a Fiesty disc as thats all I have. Started up machine and it started loading, but before it could get to the desktop, the ole X is broken gray window pops up, then after I click ok I get the ole command line. Iguess this is where I'm supposed to reconfigure, but this is live cd:confused:
So what should I do? CD is out now and booted back into Gutsy with the black bar still here ( I am having to work around it )
I really need a little assistance: should I try the ATI card I have, reconfigure X or fresh install (rather not that)

EDIT: I just tried a Kubuntu live cd and it went all the way to desktop and there is NO black bar
I feel a little better about this. Shall I boot up again and go into grubv an d reconfigure X? If so, what is the code as I have forgot, it's been so long since i've had to reconfigure X

---

### Post by DBeta on 2007-09-08
Interestingly enough, the exact same thing happened to me yesterday, and to top it off, I'm running a i810 chip as well. I think there was an update that killed the drivers or something. Booting from the live CD of the version I installed(7.10 Flight 5{I think}) runs fine. I've tried reinstalling the i810 driver with no luck.  It's a real pain.

Just to prove it is X acting up, if you press Alt+Ctrl+F1, there are no problems, it displays without any issues.

If I had to guess, I would say that you updated your machine, but didn't restart, so when it came back up after the power outage, it finished the install of the update, doing whatever the hell it did to X. I'm far from a Linux master though, so it is only a guess. I'd really like to get this solved fast, I'm trying to setup a Mythbox and I know my TV card is going to be enough trouble, so I don't like having to sidetrack myself self over such a silly but frustrating problem.

---

### Post by Wiebelhaus on 2007-09-08
OMG it totally screwed up your theme!


seriously man , you just killed my eyes.

---

### Post by DougieFresh4U on 2007-09-08
Gee, thanks:(
I am trying to save my system. I just reconfigureds X and still the same. When I used the Kubuntu Live-CD, the black bar was gone and all looked good. So I don't believe it to be a hardware problem.
Please help me to get my system correct. I do not know what else to try

---

### Post by DougieFresh4U on 2007-09-08
Any one, please help me save my system

---

### Post by tgalati4 on 2007-09-08
Many on-board video cards share memory with main RAM.  Perhaps the power outage zapped your BIOS such that you are not sharing enough video RAM.  That might explain the black bars.  Go into BIOS and change the video RAM to something useful like 32 MB or 64 MB, or whatever your original value was.  Save the values and reboot.  Try different values until you have exhausted your patience or the problem gets fixed.

---

### Post by DougieFresh4U on 2007-09-08
I am very glad for your reply, thanks. My machine is an older Intel. I booted a live Kubuntu CD last nite and there were no black bar.  Is some thing gone wrong with my install? I just did a Feisty live CD and no black bar as well, but when I boot into regular system, black bar is back

---

### Post by bodhi.zazen on 2007-09-08
Thread closed at OP request.

---

