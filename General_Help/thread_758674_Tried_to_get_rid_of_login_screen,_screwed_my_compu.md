---
title: "Tried to get rid of login screen, screwed my computer..."
date: 2008-04-18
forum: General Help
---

### Post by jtreach on 2008-04-18
I'm not sure what to do (It appears to load up but the screen is split into five pieces with five mice and there are some freaky effects gong on) but I thought I could install the hardy heron beta instead of trying to fix the problem. Is there any way I can do this and still preserve everything on my hardrive?

---

### Post by kirsis on 2008-04-18
What exactly were you doing, that resulted in this behavior?

---

### Post by jtreach on 2008-04-18
I tried to follow your guide but when I got to one of the commands it said it was going to remove some programs (500mb worth) I rolled with it but the next time i started my computer the desktop was heavily distorted. I have tried moving the script back as you said at the bottom of your guide but to no avail.

---

### Post by mister_pink on 2008-04-18
If you're going to reinstall then I suggest you boot a live CD and start backing things up. That said, there is a little known feature of the installer that means if you manually tell it to install onto a partion that already has ubuntu on it, it detects this and will preserve your /home folder. Be very careful here - I'd still backup onto another drive, and don't assume that its going to do it - if its detected a /home folder it will ask you if you want to keep it - if it doesn't ask it will overwrite everything because it means it hasn't detected it.
Final disclaimer - I've never used this myself, just read about it somewhere the other day.

---

### Post by kirsis on 2008-04-18
Try doing a "sudo aptitude reinstall ubuntu-desktop", see if that helps. If not, then apt-get has removed who-knows-which package, so I suggest a reinstall at that point.

Sorry to hear your system broke man. In the future don't just let apt-get remove packages, take a look at what it wants to remove and find out if they're critical to your system working as you want it to.

Good luck

---

