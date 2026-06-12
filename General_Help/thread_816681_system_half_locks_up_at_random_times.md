---
title: "system half locks up at random times"
date: 2008-06-02
forum: General Help
---

### Post by TheSeanKelly on 2008-06-02
Running Ubuntu Hardy-GNOME with compiz fusion.

I've been having issues a couple times a day with the system sort of locking up and requiring a full shut down/restart.  The biggest problem is that the lockups are seemingly so random I can't figure out what is causing them.  It seems that the first symptom is a loss of sound, but not in a way that necessarily suggests the sound is the culprit; its merely what I notice first.  From there, things fail to open.  I'll click the firefox icon on AWN, it'll bounce, nothing happens.  I open a terminal with my keyboard shortcut and it comes up, I never get the prompt, and it tells me to force quit.  The GNOME menus are all nonresponsive.  I alt-control-backspace to reboot GNOME, as that's my only option at that point.  (In the meantime, btw, whatever's open is functioning fine.  I could be chatting on pidgin this whole time with no issue, its only new things I try to open that don't work once the problem starts).

I log in, and I get a nice blue background with a cursor in the middle, then a gray box in the top left of the screen and nothing happens.  The only solution is to fully shut down/restart the computer, simply restarting gnome never works.

I've just recently started to run dual monitors with the nvidia control panel, but im 99% sure this problem has been happening before I added the second monitor, but I suppose my memory COULD be failing me about that.

I'm kind of new to linux, so I'm not sure about what appropriate things I should post to help diagnose the problem, and even if I did seems like I couldn't get to them at the time of the crash.

I don't know what I can do to reproduce the crash, it just happens when it wants to.

Any ideas?
Thanks for your time

---

### Post by cmnorton on 2008-06-04
Would you post some information about your hardware including the amount of RAM you could have and currently do have?

---

### Post by TheSeanKelly on 2008-06-04
Surely.  

Dell Latitude D820
Nvidia graphics card
2 gigs of ram
Intel Core Duo chip (1.83ghz)

I reinstalled hardy yesterday and got the problem again today.  I had been working on track tag editing in amarok, and am becomming more suspicious that the problem is related to pulseaudio and maybe amarok.

---

### Post by werries on 2008-06-04
what driver are you using for the nvidia card?

---

### Post by TheSeanKelly on 2008-06-06
Nvidia driver version 169.12

---

