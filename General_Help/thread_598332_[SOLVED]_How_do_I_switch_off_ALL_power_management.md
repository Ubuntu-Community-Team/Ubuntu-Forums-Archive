---
title: "[SOLVED] How do I switch off ALL power management?"
date: 2007-10-31
forum: General Help
---

### Post by chrismyers on 2007-10-31
I have recently built a Gutsy machine that we are using as an information wallboard. Firefox (with the 'tab slideshow' plugin)constantly updates information for our team & informs us of possible problems.
[COLOR=blue]
**However - After about 2 hours the screen blanks. :mad:**[/COLOR]

I have put 'computer sleep' & 'display sleep' to never. I have also set the BIOS to disable any power management.

I know it not the screensaver activating, because I have set the screensaver to 'plasma'.

What else can I do to prevent the screen blanking?

Many thanks.

---

### Post by pgmer6809 on 2007-10-31
Does the screen blank on other OS's? Some screens these days have their own built in power management.  Could it be that your screen is smart enough to act on its own?

---

### Post by bingoUV on 2007-10-31
can you try the solution listed here [http://ubuntuforums.org/showthread.php?t=596208](http://ubuntuforums.org/showthread.php?t=596208) ?

---

### Post by chrismyers on 2008-01-11
Many thanks.
 
The following worked for me:
 
xset -dpms

---

