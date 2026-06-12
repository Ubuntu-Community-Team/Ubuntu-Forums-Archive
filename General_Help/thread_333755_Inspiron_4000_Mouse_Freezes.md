---
title: "Inspiron 4000 Mouse Freezes"
date: 2007-01-07
forum: General Help
---

### Post by RippyMan on 2007-01-07
Hi All,

I have recently installed Ubuntu Edgy on an old Dell Inspiron 4000 laptop. It has 1 ghz processor and 256mb ram. Anyway, everything is working pretty well on this laptop except for the mouse. Occasionally the mouse pointer will intermittently freeze in a certain spot on the screen for less than a second and then jumps to the edge of the screen. It mostly does this during instances where there is a load on the processor, especially with Firefox, but also in other applications as well such as Kaffeine. I haven't a clue what could be causing this, but perhaps it is caused by some power setting or something. It did the same thing in Dapper, only it was worse. I was wondering if anyone else had this problem with Ubuntu on this laptop and possibly found a solution for it. I highly doubt the problem is caused by the computer's less than stellar hardware specs, as I have Edgy running on two computers that are even more underpowered (a 800 mhz desktop and a 500 mhz :o Latitude CSx), both of which do not have this same problem. It is also not a hardware problem, as it did not have this problem with Puppy Linux and (gosh I hate saying this!) Window$ XP. It is also not a touchpad only issue, as it did it with a USB mouse also. Any help on this would be greatly appreciated, especially since it will be used by a new Ubuntu user, my mom. 

Thanks in advance for your help,
RippyMan

---

### Post by RippyMan on 2007-01-08
I absolutely loath bumping posts, but does anyone have any possible solutions to this problem?

---

### Post by tito2502 on 2007-01-08
Could it be that you are moving the cursor as the CPU load increases?

The cursor is still mving but it is not displaying every step of its movement.

---

### Post by RippyMan on 2007-01-08
tito2502, thanks for your reply. I realize that I am moving the mouse around when the CPU is under load. What you said is probably what is happening. However, I find it odd that it does this on the 4000 but not on lower-powered computers such as the two I mentioned. I've loaded the same page in Firefox on the 500mhz and on the Inspiron 4000. I'm able to move the mouse around just fine on the CSx, but not on the 4000. I realize there probably is no solution to this problem, but I thought it was worth asking about. Personally it doesn't bother me, but I'm afraid it may give my mom a bad impression of Ubuntu.

---

### Post by night-hawk on 2007-01-14
RippyMan, 

I have the same laptop (Inspiron 4000) and also had the same problem.   I fixed the problem by following the steps at the page below: 

_[HOWTO: Double Clock Speed Problem]("http://ubuntuforums.org/showthread.php?t=75281")_

(Scroll down to the 32-bit section.  Since we have the same laptop I'll save you the guesswork and tell you which option worked for me:  "acpi=off")


ALTERNATIVE SOLUTION

Another (much easier :D ) way I found for fixing the problem is the following:  
On your desktop go to "System --> Administration --> Services"  and disable "CPU Frequency manager (powernowd)"  and reboot the laptop.

---

### Post by RippyMan on 2007-01-15
night-hawk, thank you for posting that solution! I was beginning to believe that it was entirely unrepairable. I will try acpi=off on the livecd and see how that goes. Thanks again!

---

