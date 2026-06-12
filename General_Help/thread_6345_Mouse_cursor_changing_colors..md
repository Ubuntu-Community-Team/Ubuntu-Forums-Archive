---
title: "Mouse cursor changing colors."
date: 2004-11-27
forum: General Help
---

### Post by indygreen on 2004-11-27
I'm having a very confusing issue with the mouse cursor on my desktop machine.  Out of nowhere, the mouse cursor will turn black, stay that way or an undefined amount of time, and then will turn back to white.  For the life of me, I cannot figure out why it's doing this.  I use the color black as my desktop color so when the cursor turns black, it becomes lost.  This doesn't happen on my laptop and it didn't happen on this desktop machine when I was running Slackware.

Thanks for the help.

---

### Post by Rancoras on 2004-11-27
What is your hardware on the troublesome machine?  Specifically, the video card.  You might need to edit /etc/X11/XF86Config-4, add 'Option "SWCursor"' to the Device section, save, and restart X.

---

### Post by indygreen on 2004-11-28
Thanks for the help.  I think that fixed the issue!

:)

By the way, the video card is a ATI Rage 128.

---

