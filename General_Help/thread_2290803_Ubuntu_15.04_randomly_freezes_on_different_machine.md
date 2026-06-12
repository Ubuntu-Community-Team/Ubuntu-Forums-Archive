---
title: "Ubuntu 15.04 randomly freezes on different machines, mouse cursor keeps working"
date: 2015-08-15
forum: General Help
---

### Post by cornellg on 2015-08-15
I have been experiencing identical random freezes on two different machines at two different locations:

**Computer 1**: This was running ubuntu 12.04 LTS with KDE and the freezes were very occasionally occuring. I upgraded to 15.04 (64 bit) with KDE and for a short while everything seemed fine. Plasma has become a pain however, so I switched back to unity, or whatever it is called now - "ubuntu" in the login screen. Lately the freezes have started occuring again though. Don't remember if they occured running KDE. They seem to have become more frequent after I installed lots of extra packages to get stuff like Dropbox, Wacom tablets and dual monitors working correctly. The machine froze at least once before those extra installs.

Processor: Intel Core i7 CPU 920 @ 2.67GHz x 8
Graphics: GeForce GTX 260/PCIe/SSE2
Kernel version 3.19.0-25-generic.

**The freeze**: Sometimes preceded by a short freeze, the pc will become unresponsive. Ctrl-Alt-Del, Ctrl-Alt-Backspace, Ctrl-Alt-F1 will not work. Can't remember if keeping a key pressed results in any sound responce. **The mouse cursor will still move, but not click** (or at least not show any sign of it). This goes for the Wacom tablet too.

The screen does not go blank or black, just remains as it was before the freeze. I often run Youtube on Chromium on a different workspace for music. That sometimes keeps playing and I think, but am not sure, that it sometimes stops after a short while. As it is not on my active workspace, I cannot see whether that is due to being preloaded or not. Also I don't know about the video, just the audio.

The freezes seem to be at random moments and I haven't been able to find a correlation with running any programs, though it sometimes seemed to result from playing with browser tabs. That may be coincidence though, as the freezes also seem to occur when no browser is open (not sure though, will start to keep better track from now on). EDIT It does indeed sometimes happen without and before any browser is loaded.

**Computer 2**: This pc does not share any hardware with computer 1. I had ubuntu 12.10 with KDE on it, and the freezes became so annoying that I decided to upgrade. This was no longer possible however, so I did a clean install of 15.04 (64-bit), keeping home folders intact. The pc is at another location and has a different ISP. On this pc I did not reinstall KDE and left it running as a "plain" ubuntu pc.

Processor: Intel Core i7-3770 CPU @ 3.40GHz x 8
Graphics: Gallium 0.4 on NVE7
Kernel version 3.19.0-25-generic.

**The freeze**: Identical to computer 1, which I find baffling, as I don't see other people reporting this and the computers have very little in common other than both having Wacom tablets, which are different models). I don't know if Youtube would keep playing on this machine - never use it here, though I do use Chromium here too.

What additional information can I provide to help solve this issue, and how do I go about getting it? Are there relevant logs to be found? Thanks for your help!

---

### Post by freeman2 on 2015-08-22
Same here. My desktop pc has the same symptoms, but my laptop, also running ubuntu 15.04 has no problem (yet).
I have made the exact same observations but can add that it is not related to the browser, it occurs with firefox, or chrome, or without any browser running.
I have two errors "system program problem detected", one is about cups, the other is colord_sane.
A look at the log in /var/log/apport.log seems to confirm it is colord_sane that causes the freezes, but there are a lot of red warnings, mostly related to gnome stuff.
I have tried to log using the gnome interface, not gnome-classic, and it seems to keep it together.

I have ran the full memtest and found no error.

I might install debian to test it out.

---

### Post by rlees42 on 2015-08-23
I have identical behaviour.  Nothing fancy about my system like a wacom tablet, etc.  I'm a bit of a newbie with error tracking so I'm afraid I can't provide any log information on my own - but if anyone is chasing this bug and wants my system info just contact me and let me know what they want.

<edit> google searching for this also yeilded a wiki page addressing this issue:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
indicating that each user should submit a separate bug for this and logs that should be collected.  I'll probably do that, I suppose you could too.

---

### Post by wmeier on 2015-08-23
Similar problem using Lubuntu 1504 except usually the mouse pointer freezes.

---

### Post by cornellg on 2015-08-24
So does anybody have an idea what to do about any of this?

wmeier, before I posted, I checked to see if anyone else was experiencing this. I came across a few that had freezes including the mouse pointer, so you may want to look for those as your freezes might better fit their description.

---

### Post by cornellg on 2015-08-26
Just to make sure, on computer 2 I removed both cups and sane, including the extra packages that were automatically marked for removal. This pc does not have a scanner or printer, so it should be fine without them. I'll wait and see if the freezes still occur.

---

### Post by cornellg on 2015-11-04
Sadly, the freezes persist despite removing cups and sane. Will upgrade to 15.10 soon and hope that that will fix it, though that seems unlikely as the freezes previously survived upgrading through four new versions and a clean install upgrade spanning five new versions. Sigh...

I really wish someone could help by telling me how better to pinpoint the source of the trouble.

---

