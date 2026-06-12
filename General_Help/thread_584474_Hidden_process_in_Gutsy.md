---
title: "Hidden process in Gutsy?"
date: 2007-10-21
forum: General Help
---

### Post by Senesence on 2007-10-21
There is this strange thing happening since I upgraded to Gutsy, where my mouse cursor seems to skip/lag (*for lack of better words*) every 2 seconds - almost exactly.

It's barely noticeable when nothing else is running, but the lag in mouse movement is definitely there, and it becomes even more obvious when more than one program is running simultaneously.

Due to the precise timing in mouse skips/lag, I figure it must  a process in action. However when I use the gnome system monitor or the command line "top" utility, I can see no other processes running except for the program I'm using to actually observe process activity.

Is there some new, hidden process in Gutsy (or the new kernel maybe) that does something every 2 seconds?

Also, how can I view hidden processes?

---

### Post by ash1574 on 2007-10-21
What is your processor clocked at?

---

### Post by RTrev on 2007-10-21
> **Senesence said:**
> Also, how can I view hidden processes?

Hidden processes??  I didn't know there were any.  If there were, wouldn't we be talking about a rootkit?

---

### Post by Flyn on 2007-10-22
I'm having this problem as well, dmesg reveals that my Touchpad is losing sync, I've also noticed that the hard drive makes wierd noises when this happens. Also, this is not a hardware issue, since I also dual boot Vista which has no issues whatsoever (except being Vista ;-))
This started yesterday, maybe when I upgraded some components.
 
Any suggestions? Gutsy is unusable as it is.

---

### Post by Flyn on 2007-10-22
I've removed apparmor, the problem appears to be solved.
Try ```
sudo apt-get remove apparmor
```.

---

### Post by Flyn on 2007-10-22
Or it could be removing sensor modules that did the trick, not sure.
In any case, I also removed :
i2c-i801
eeprom
p4_clockmod
coretemp

And now everything seems to be ok.

---

### Post by therealknewman on 2007-10-22
I'm having a similar problem with processing power that is causing a major slowdown. While thankfully my cursor isn't jumping around, I am having difficulty scrolling in programs such as gThumb, Firefox, Amarok, and many others. Pretty much any program that involves graphics of some sort has major trouble with scrolling up or down. I have also noticed a significant slowdown in Compiz-Fusion. Back in Feisty everything was flyin with the exact same hardware setup, AMD 3800+ (x64 version of ubuntu installed) 1 gb of ram, radeon x1600pro, all running on a seperate 80 gb harddrive. So why the slowdown in Gutsy Gibbon?

---

