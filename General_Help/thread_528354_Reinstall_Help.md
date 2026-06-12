---
title: "Reinstall Help"
date: 2007-08-17
forum: General Help
---

### Post by RTFishUL on 2007-08-17
Ok, so I've given up on a problem of mine and I'm fine with a fresh reinstall.

Problem is, my problem only allows me to boot into recovery mode, I can not boot a live cd.

I thought I'd try to burn the iso of the text install cd, but I'm having trouble doing that in recovery mode, it doesnt appear to recognize any external devices (external drives, flash drives, cds, etc)

I need help, I just want to do a full reinstall of the entire OS, I have my files backed up elsewhere

---

### Post by Happy_Man on 2007-08-17
......I'm confused. Could you explain in greater detail?

---

### Post by RTFishUL on 2007-08-17
Ok, the entire story:

Not sure what caused the issue, but when I boot everything goes normal through the boot screen. Then right afterwards the Nvidia logo shows up as it usually does, but the screen goes dark grey before the login screen comes up.

I can however boot into recovery mode.

I couldn't find a way to solve this problem, so I decided to just screw it and reinstall... but booting from a live cd has the same problem as booting from my hard drive, the grey screen.

I can't do the usual ctrl + alt + 1 to go into a terminal, in fact it seems like my mouse and keyboard arent functioning at all during this grey screen thing.

They do work in recovery mode though.

So I need to know how to reinstall ubuntu completely without the live cd... I think the alternate cd may work, but I'd have to burn that, and recovery mode doesnt recognize cd's in my drive.

Or I could get the grey screen problem solved, not sure on that one though.

---

### Post by merlinus on 2007-08-17
Two ideas.

First, in recovery mode, can you get into System/Administration/Login Window/Security and tick Enable Automatic Login?

If that works, then the login window will be bypassed upon bootup.

Second, perhaps it is related to your monitor rather than the video card?

-merlin

---

### Post by RTFishUL on 2007-08-17
Can't get to the auto-login option, says GDM isn't running.

I guess it could be related to my monitor, but that would surprise me because everything works perfectly fine in recovery mode.

---

