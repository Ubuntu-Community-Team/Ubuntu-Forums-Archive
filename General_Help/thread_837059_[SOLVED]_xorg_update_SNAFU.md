---
title: "[SOLVED] xorg update SNAFU"
date: 2008-06-22
forum: General Help
---

### Post by letired on 2008-06-22
Just now I installed the kernel update (*.14->*.15) and with that, the xorg/xserver updates. Upon restart, it seems all my old settings have been wiped, and, considering it took me a few DAYS to make this work in the first place, I would very much like a quick fix such as "restore that <snip>" or just some way to backtrack and undo whatever changes have been made.
I'm on 7.10, the problem ultimately lies in the gfx accelerator, a GeForce 8600M GT. Currently I'm down to 800*600 resolution and that wonderful prompt at boot, "display settings are <snip>, what do you wanna do?".
Thanks in advance.

---

### Post by PmDematagoda on 2008-06-22
Now to your problem, how did you setup the Nvidia card in the first place?

---

### Post by letired on 2008-06-22
> **PmDematagoda said:**
> Now to your problem, how did you setup the Nvidia card in the first place?

I apologize for the language, I believe it comes from not being a native speaker and/or from watching lots of Sopranos in the last few days.
Anyway, as I remember it, I followed the steps in [this](http://ubuntu-bossieman.blogspot.com/2007/03/nvidia-igen.html) (it's in Swedish, but I reckon the important parts are in linux-speak anyway) blog post, as opposed to just using restricted drivers (after having tried restricteds and failed). 
I also remember, after having executed the script properly, having to search for other people's xorg.conf on google and copy-pasting a whole bunch of lines into my own xorg.conf. This last bit enabled me to choose the appropriate settings in xorg (1440 by 900 and 60Hz) which were previously not available in the drop-down menus. Also, until these changes were made, activating desktop visuals caused X to crash.

---

### Post by spiderbatdad on 2008-06-22
generally, before overwriting a file, the system makes a backup. Have you looked in /etc/X11/ for an xorg.conf<some date>

---

### Post by letired on 2008-06-22
> **spiderbatdad said:**
> generally, before overwriting a file, the system makes a backup. Have you looked in /etc/X11/ for an xorg.conf<some date>

Excellent, I found the old xorg.conf, renamed to xorg.conf.backup.nvidia . It would seem that the script I ran to get the drivers pertains to a specific kernel and so must be rerun after a kernel update. I'll try this, and then somehow pointing to the backuped xorg.conf. Would it simply be a matter of renaming xorg.conf.backup.nvidia to xorg.conf?

---

### Post by spiderbatdad on 2008-06-22
> **letired said:**
> Excellent, I found the old xorg.conf, renamed to xorg.conf.backup.nvidia . It would seem that the script I ran to get the drivers pertains to a specific kernel and so must be rerun after a kernel update. I'll try this, and then somehow pointing to the backuped xorg.conf. Would it simply be a matter of renaming xorg.conf.backup.nvidia to xorg.conf?
Yes. simply rename the backup to the original. Of course, you'll cheat yourself out of all that great experience of re-writing and configuring xorg.conf manually...

---

### Post by letired on 2008-06-22
Oh lawd, it worked! And it barely took two hours, hallelujah. Thank you all.

---

