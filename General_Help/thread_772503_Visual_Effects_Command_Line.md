---
title: "Visual Effects Command Line"
date: 2008-04-28
forum: General Help
---

### Post by Matthileo on 2008-04-28
Is there any way to enable/disable Ubuntu Visual Effects from the command line?  I'd like to include a command to disable them in the launchers for my opengl apps so i don't have to go to settings every time to change it.

---

### Post by Tomatz on 2008-04-28
> **Matthileo said:**
> Is there any way to enable/disable Ubuntu Visual Effects from the command line?  I'd like to include a command to disable them in the launchers for my opengl apps so i don't have to go to settings every time to change it.

To stop compiz and replace it with the gnome window manager:

**metacity --replace**

to restart compiz:

**compiz --replace**

or use this:

[http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)

disable desktop effects in the preferences menu then install the .deb and add the command **fusion-icon** to **sessions, startup**. Then you will have a nice tray app to switch between window managers. ;)

---

### Post by al090187 on 2010-05-09
Do you know of any way to make the computer auto-switch to, basically no visual effects when it is on battery power, and then to switch back to the previous plan when plugged in again?

I'm sure there is a way for the commands mentioned above to be called when the AC adapter is pulled, just need pointing in the right direction.

---

