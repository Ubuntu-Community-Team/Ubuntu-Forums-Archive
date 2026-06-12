---
title: "how do I get my monitor out fn key to work?"
date: 2007-04-08
forum: General Help
---

### Post by harty83 on 2007-04-08
I have a laptop in which the fn-f4 key is suppose to toggle between an external monitor and the internal LCD.  Mine works in Windows but not in Ubuntu.  My understanding is that it is controlled by acpi.

Is it possible that the key is just not mapped to the correct script?  Any clue on how I can get this to work?

I have an Intel 945GM video card.  I have tried a patched version of i810switch.  It outputs to the CRT but it is fuzzy, only shows half the screen, and pretty much disables the controls on my monitor.

---

### Post by jpeddicord on 2007-04-09
The laptop should be controlling this on its own and not the OS. If you are having flickering screen problems when switching over to the CRT, try lowering the resolution and/or changing the refresh rate. I had similar problems that were fixed by that method.

Jacob

---

### Post by harty83 on 2007-04-09
> **jacobmp92 said:**
> The laptop should be controlling this on its own and not the OS. If you are having flickering screen problems when switching over to the CRT, try lowering the resolution and/or changing the refresh rate. I had similar problems that were fixed by that method.

Jacob

Thanks for answering Jacob.  The fn-f4 combination works fine under Windows XP (I dual boot).  It will not work however under any form of linux.  

I can get a dual monitor with clone and xinerama to work fine.  But sometimes I just don't want to fool with restarting x to switch between a single and dual configuration.  I guess it could be a refresh rate issue but shouldn't since I can switch between the two (LCD and CRT) flawlessly under windows.  I can also use the same resolution on both laptop and external monitor with no problem.  

The only time I have gotten this to work is when I updated my BIOS.  But then, under linux all my other function keys were messed up.  It was like it was set to do something other than what the keyboard indicated.  For example, my fn-f7 normally dims my brightness but when I did the bios update, it exported to an external monitor!  So I know that it at least works, but something was obviously wrong.  Under windows with the bios update, everything worked flawlessly as they were suppose to.  Since I couldn't use any of my other function keys in linux, I downgraded my bios which fixed everything, but again fn-f4 does nothing when it is suppose to export to an external monitor.  

When the fn-f4 works under windows but not under linux, this tells me that it has something to do with the OS.  At what level that something is, I have no clue.  But what other conclusion can I come to?

Can anyone think of anything else I can try?

---

