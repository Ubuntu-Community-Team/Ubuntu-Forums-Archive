---
title: "GUI Issue XFCE environment, Ubuntu 12.04"
date: 2014-07-27
forum: General Help
---

### Post by anachronism2 on 2014-07-27
I'm stumped and I'm an uber-noob, so please go easy on me. This happened after I put my computer in hibernate, without closing the web browser first. 

-XFCE DE 4.8
-Ubuntu 12.04
   -Toshiba Satellite C655D-S5511  

I'm unable to open any programs graphically, and I can't switch to a different terminal (if that's the right word for the Ctrl-Alt-F1 etc shells). I'm typing this within the standard Ubuntu environment, and I can't access any other terminals from here, either. I am able to open the BASH from XFCE with a keyboard shortcut, and that's about it.

---

### Post by egeezer on 2014-07-27
It is a bit crude as a method, but you could try Ctrl+Alt+SysRq+b to give you a reboot (not quite as crude as a cold stop, but close)

Or you could be gentle, stretch your hands, and do Ctrl+Alt+SysRq+REISUB.  Press the first letter, wait a couple of seconds, then the next - and do the same right to the end. The final b reboots

---

### Post by mooreted on 2014-07-27
You could also do:

CTRL+ALT+F1

That will get you into a single user session. Login with your username and password then do:

sudo reboot

---

### Post by anachronism2 on 2014-07-27
Sudo reboot and ctrl-alt-sysrq-b did nothing. Sysrq is a function key though, but fn+sysrq+b took a screenshot

---

### Post by Bucky Ball on 2014-07-27
I'd bite the bullet and hard shutdown if you nothing else is working. It sounds like a chronic hang.

How much RAM do you have installed and is your /swap partition the same size or larger? If you are hibernating and your /swap partition is less than your RAM, that is probably your issue, especially if you had a few things open when this happened (and if you have minimal RAM and small swap that could be Firefox and ten tabs).

PS: I've attached your large screen shot in the first post. Please attach them using either 'Go Advanced' or 'Adv Reply' and clicking the paperclip icon. Cheers.

---

### Post by Dennis N on 2014-07-27
> **anachronism2 said:**
> Sudo reboot and ctrl-alt-sysrq-b did nothing. Sysrq is a function key though, but fn+sysrq+b took a screenshot

The command should be **Alt+SysRq+B**, but before this you should do this with the R, E, I, S, and U keys, and then B.

see: [http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

This should be a last resort. If you can get the terminal, then shutdown or reboot, is probably better.

---

### Post by Bucky Ball on 2014-07-27
> **Dennis N said:**
> 

This should be a last resort. If you can get the terminal, then shutdown or reboot, is probably better.

+1. Anything definitely better than a hard shutdown.

---

### Post by mooreted on 2014-07-27
Sometimes it gets to the point where you just have to pull the plug and hope for the best.

---

### Post by anachronism2 on 2014-07-27
Even a hard reboot didn't work. At least I still have my data and other DEs. Thanks for the idea, though, 
everyone

I may dam well have to uninstall and reinstall the whole XFCE environment. I scooched Windows way over, and Ubuntu has more than enough ram. Weird

---

### Post by mooreted on 2014-07-28
Try deleting 

~/.cache/sessions

That is where Xfce stores saved sessions.

---

### Post by anachronism2 on 2014-07-30
@mooreted This worked with the rm -f -r command. Thanks!

How to mark solved from mobile?

---

### Post by Bucky Ball on 2014-07-30
Thread Tools at top right and 'mark thread as solved'. Good work and enjoy! ;)

---

### Post by mooreted on 2014-07-31
> **anachronism2 said:**
> @mooreted This worked with the rm -f -r command. Thanks!

How to mark solved from mobile?

Awesome, glad that worked for you.

:)

---

