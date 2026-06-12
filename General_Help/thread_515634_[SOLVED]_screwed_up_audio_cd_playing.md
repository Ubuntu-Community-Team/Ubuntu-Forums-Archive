---
title: "[SOLVED] screwed up audio cd playing"
date: 2007-08-02
forum: General Help
---

### Post by fuscia on 2007-08-02
so, one day, i just popped the cd out without clicking on the cd icon and selecting *eject*. since then, i've had trouble playing cds. the cd will be recognized and identified, and even played by kmplayer, but audacious won't play it and kmplayer won't play it from a file manager. when i clicked *check drive* in audacious, it recognized the drive, the cd and even the number of tracks on the cd, but it said it failed to check */mnt/cdrom*. what shall i do to fix it?

---

### Post by twiggyness2000 on 2007-08-05
> **fuscia said:**
> ...but it said it failed to check */mnt/cdrom*. what shall i do to fix it?

I'm not sure what distro your using, but my Gnome-Feisty install mounts the CD in */media/cdrom* instead of */mnt/cdrom*.  I had to change the path in Audacious CD Audio Plugin preferences to reflect that.

Edit: Also check your setting for digital audio extraction...try Digital first and then Analog
Good Luck

---

### Post by fuscia on 2007-08-07
> **twiggyness2000 said:**
> I'm not sure what distro your using, but my Gnome-Feisty install mounts the CD in */media/cdrom* instead of */mnt/cdrom*.  I had to change the path in Audacious CD Audio Plugin preferences to reflect that.


that's it! thank you, much.

---

