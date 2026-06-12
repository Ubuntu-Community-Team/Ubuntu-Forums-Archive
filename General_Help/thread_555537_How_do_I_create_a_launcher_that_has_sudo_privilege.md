---
title: "How do I create a launcher that has sudo privileges?"
date: 2007-09-20
forum: General Help
---

### Post by mjpatey on 2007-09-20
I'm trying to run the following:

```
sudo env WINEPREFIX="/home/mjpatey/.wine" wine "C:\Program Files\Softouch\EasyWorship2006\EasyWorship.exe"

```

This is one of those programs that only exists for Windows, and I use it at church, so at home I have to run it under Wine.  It runs flawlessly under Wine, by the way.  :-)

The code above, when entered into a terminal, launches the program just fine.  If I don't include "sudo", the program tells me I don't have sufficient privileges to run it.  But when I try to make a launcher with that code and double-click it, nothing happens.  If I leave out the "sudo", at least I get the same "insufficient privileges" message, but it still won't run.

Is there some way to give a launcher sudo privileges?

-Mark

---

### Post by zekica on 2007-09-20
You should never have to run normal applications as superuser, but if this application doesn't work with your current privileges, you can make it run as root.

Instead of 'sudo' type 'gksudo' in the launcher, and see if that works.

---

### Post by mjpatey on 2007-09-20
I thought it was weird, too.  As far as I know, under Windows, the program can be installed for any user, regardless of privileges.  Maybe it's a Wine thing?

In any case, your suggestion worked!  I changed "sudo" to "gksudo" in the launcher, et voila!  It asks me for my password, and I'm in.

Thank you!

-Mark

---

### Post by Nehvrook on 2007-09-20
Did you use sudo in the command line when you were installing it? If so that might be why you can't run it as a normal user.

---

### Post by mjpatey on 2007-09-20
That's it!  I did use sudo when installing... I'd had trouble with installing a previous program under Wine, and for some reason it worked when I ran the installer with "sudo wine..." so I installed this program the same way.

This also explains why the launcher created automatically by the Wine install process has a padlock on it, and belongs to root.  I can't, even as root, change the owner to me.

Well, when I upgrade to Gutsy in a few weeks, I'll be re-installing this program, and will do so without sudo.  Thanks for the insight!!!

-Mark

---

