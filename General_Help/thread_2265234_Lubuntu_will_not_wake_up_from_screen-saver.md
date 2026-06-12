---
title: "Lubuntu will not wake up from screen-saver"
date: 2015-02-13
forum: General Help
---

### Post by Brent_Santin on 2015-02-13
Hi,

When I walk away from my computer installed with Lubuntu 14.04.1, after about 10 minutes the screen goes into screensaver mode (black).  Most of the time it will "wake up" by moving the mouse, touching the keyboard, etc.
Then it asks me for a password, and everything is good.  **NOTE: this is not a hibernation or standby mode, I am pretty sure I have standby disabled. It's merely screensaver mode (with perhaps monitor power saving enabled).**

But about 1 time in 5 the computer will "wake up" to a black screen.  The powered off monitor wakes up, but only displays a black screen.  Hard to describe, but it is the difference between how a monitor looks when it is truely off (shut down) and when it is displaying the colour black (which is a very dark grey).  Also the LED on the monitor turns solid so I know it's receiving a video signal from the "woken up" computer.

But I cannot get past the black screen.  I cannot make the desktop show up again.  No key combination or mouse movement will restore the Lubuntu desktop.

The ONLY thing I can do is press the power button on my computer, which then "wakes up" Lubuntu by sending it into shut-down mode (i.e. the Lubuntu logo shows up on the monitor with the dots beneath it, and the computer turns off as if I had manually shut down).  Of course, when this happens I lose whatever I had been doing on open applications.

It's a pretty frustrating thing to have happen.  I've tried disabling the "Switch Off Display" feature in Light Locker settings.  I don't really want to disable Light Locker's screen saver as I would like to have some sort of screen saver to prevent burn-in on my monitor.

I don't think Power Manager has anything to do with this problem because I'm using a desktop system, and when I try and open the Power Manager preferences GUI I get the message: **"Xfce4 Power Manager is not running, do you want to launch it now?"**

Any ideas on why my computer won't occassionally wake up?  The ONLY theory I have is it might be happening when the computer falls asleep while I have an open application window on screen (i.e. web browser).  I'm not sure if that's always the case though, as I didn't pay close enough attention before this behaviour start on whether I always had an application open when the computer went into screensaver mode.

---

### Post by Dennis N on 2015-02-13
This could be caused by the DPMS system. See post #4 of this thread for more information:

[http://ubuntuforums.org/showthread.php?t=2262763](http://ubuntuforums.org/showthread.php?t=2262763)

Note: Lubuntu uses the xfce4 power manager, so the post also applies to Lubuntu.

---

