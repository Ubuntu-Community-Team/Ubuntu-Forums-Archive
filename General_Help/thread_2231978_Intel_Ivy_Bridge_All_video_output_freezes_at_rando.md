---
title: "Intel Ivy Bridge: All video output freezes at random while watching videos"
date: 2014-06-29
forum: General Help
---

### Post by dalekky on 2014-06-29
This happens completely at random and as such is not reproducible at will.

I don't know if it ONLY happens while playing video files. But it is MOST noticeable during video viewing because the screen freezes.
The mouse pointer can still be moved around the screen but the dash is frozen along with the rest of the screen and nothing can be clicked, nor can any keyboard input be made. Can't switch to a terminal or anything. Keyboard is completely locked up.
**EDIT: I have since found I CAN get to the screen to go blank by pressing Alt+Ctrl+F1, but that is the only keyboard combination that gets any noticeable response.

While this is all apparently frozen, the audio of the video continues to play as normal.

This all lasts about 30 seconds and then the screen and keyboard unfreeze and return to normal. The video skips instantly forward to catch up with the audio and continues to play as normal.

No errors are displayed.

So basically, it is like everything except audio and mouse pointer movement is frozen for 30 seconds for no apparent reason, then everything returns to normal.
Any clues as to what causes this and how to prevent it?

---

### Post by Habitual on 2014-06-29
How much RAM do you have installed?

---

### Post by dalekky on 2014-07-04
6Gb RAM
750Gb HDD - 2Gb swap, approx 490Gb free
Processor Intel Core i3-3110M CPU @ 2.40GHz × 4
Graphics Intel Ivybridge Mobile
Running 64-bit Ubuntu 14.04

---

### Post by dalekky on 2014-07-27
This issue is still happening. Still completely at random. Still got no idea what causes it. I can't be the only one experiencing this bug.
All video output to all attached monitors freezes except for the mouse pointer which can still be moved around on any connected screen, but cannot click or interact with anything. Can't use keyboard at all during the screen freeze. Audio continues to play as normal during the freeze, then everything unfreezes after approximately 30 seconds and everything is normal again. Annoying, unpredictable but tolerable.
Probably occurs at least once every 10 hours on average.

---

### Post by dalekky on 2014-07-27
Oh, and I never get that fade to gray screen you usually get when an application stops responding for a moment because resources are limited. This is just a straight out graphical output freeze.

---

### Post by silverslimer on 2014-07-27
> **dalekky said:**
> This happens completely at random and as such is not reproducible at will.

I don't know if it ONLY happens while playing video files. But it is MOST noticeable during video viewing because the screen freezes.
The mouse pointer can still be moved around the screen but the dash is frozen along with the rest of the screen and nothing can be clicked, nor can any keyboard input be made. Can't switch to a terminal or anything. Keyboard is completely locked up.

While this is all apparently frozen, the audio of the video continues to play as normal.

This all lasts about 30 seconds and then the screen and keyboard unfreeze and return to normal. The video skips instantly forward to catch up with the audio and continues to play as normal.

No errors are displayed.

So basically, it is like everything except audio and mouse pointer movement is frozen for 30 seconds for no apparent reason, then everything returns to normal.
Any clues as to what causes this and how to prevent it?

I'm curious as to what kind of GPU you're using and then what kind of drivers you're using with that GPU. Your behaviour seems to point in the direction of you using an NVIDIA-based graphics solution with the Nouveau drivers. Driver-wise, Nouveau is absolutely awful and to be removed in favour of the proprietary NVIDIA ones.

---

### Post by dalekky on 2014-07-27
As posted above, the GPU lists itself as Intel Ivybridge Mobile. But this GPU was working fine until upgrade to 14.04.

---

### Post by dalekky on 2014-11-18
This is STILL happening. I have still not found any cause to this bug. Has no one else experienced this?

---

### Post by dalekky on 2014-11-25
Any news on how to solve this issue?

---

### Post by mörgæs on 2014-11-25
Have you tried a live boot of 14.10? 
Many improvements for the Intel drivers have been added to the 3.16 kernel. I don't know if it solves this particular problem, though.

---

### Post by dalekky on 2015-05-06
I tried running 14.10 from live session. It would not work at all.
I tried installing 14.10 (as I sometimes find a new version of Ubuntu will not function properly unless it is fully installed). 14.10 totally killed the computer to the point it could not even boot up. Was forced to re-install 14.04 from scratch and restore from my backup.
Computer screen is still freezing randomly for no obvious reason. Further more, it now occasionally freezes for indefinite periods of time and requires a hard reset to escape.
Symptoms still the same:
 - everything on the screen(s) freezes except the mouse pointer
- can't click anything.
- any audio that was playing before the freeze continues to play as if nothing was wrong.
- keyboard responds to Alt+Ctrl+F1, but no tty terminal appears, instead a blank black screen. I've not been able to determine if any other key press or combination has any effect during the freeze. Attempting to use the keyboard to stop/start any audio that was playing at time of freeze certainly has no effect.
- freeze lasts approx 30 seconds to 1 minute in most cases, but now also freezes indefinitely on occasion.

---

### Post by mörgæs on 2015-05-07
If the bug is also in 15.04 please open a bug report.

---

### Post by dalekky on 2015-07-29
I've upgraded to 15.04, completely skipping 14.10 which killed computer outright.

So far no problems with screen freeze.

I don't know if I should mark this thread solved or not due to the nature of the issue being so unpredictable.
It might just be that I've been lucky so far to not have a freeze since the upgrade. It could still happen.

---

### Post by monkeybrain20122 on 2015-07-29
What do you mean by "upgrade"? If you use the upgrade manager then all your problems might have been yet another bad upgrade and could be fixed by a fresh install.

---

### Post by dalekky on 2015-07-30
A fresh install was not the solution, I am pretty sure I mentioned earlier in the thread that doing a fresh install of 14.04 did NOT fix the random freezing problem.
A fresh install of 14.10 killed the computer completely.
The upgrade to 15.04 was also a fresh install from the installation DVD.

---

### Post by mörgæs on 2015-08-01
I suggest that you mark the thread solved. If the problem reappear then you can just remove the mark and post again.

Please spread the word: Trying the latest release and not only the latest LTS release should be a standard procedure.

---

### Post by dalekky on 2015-08-03
Still no graphical freezes since upgrade to 15.04 so I am marking this thread solved.

---

