---
title: "[SOLVED] Nautilus fails to launch on startup"
date: 2008-03-20
forum: General Help
---

### Post by rune0077 on 2008-03-20
I'm having this weird issue, where all of a sudden Nautilus fails to be launched when Gutsy loads. This is the error message I get: 

> Nautilus can't be used now. Running the command "bonobo-slay" from the console may fix the problem. If not, you can try rebooting the computer or installing Nautilus again.

This may be the result of the latest update, or it may be because I ran the command "ldconfig" (yeah, I ran it without knowing what it did - let's call it for testing purposes). Anyway, when I run "bonobo-slay" I can then launch Nautilus and gnome-panel without any problem and things are back to normal until next reboot. I've tried reinstalling both Nautilus and the bonobo libraries, but to no avail.

Does anyone have a clue what could be causing this, and (more importantly) how to fix it?

---

### Post by Oldsoldier2003 on 2008-03-20
> **rune0077 said:**
> I'm having this weird issue, where all of a sudden Nautilus fails to be launched when Gutsy loads. This is the error message I get: 



This may be the result of the latest update, or it may be because I ran the command "ldconfig" (yeah, I ran it without knowing what it did - let's call it for testing purposes). Anyway, when I run "bonobo-slay" I can then launch Nautilus and gnome-panel without any problem and things are back to normal until next reboot. I've tried reinstalling both Nautilus and the bonobo libraries, but to no avail.

Does anyone have a clue what could be causing this, and (more importantly) how to fix it?

Try making sure your packages are up to date then reinstalling nautilus

```
sudo apt-get update
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

---

### Post by rune0077 on 2008-03-20
> **Oldsoldier2003 said:**
> Try making sure your packages are up to date then reinstalling nautilus

```
sudo apt-get update
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

Sorry, that had no effect at all.

---

### Post by markharding557 on 2008-03-20
this thread might help [http://ubuntuforums.org/showthread.php?t=693307]("http://ubuntuforums.org/showthread.php?t=693307")

---

### Post by rune0077 on 2008-03-20
> **markharding557 said:**
> this thread might help [http://ubuntuforums.org/showthread.php?t=693307]("http://ubuntuforums.org/showthread.php?t=693307")

That fixed it. Thank you ever so much.

---

