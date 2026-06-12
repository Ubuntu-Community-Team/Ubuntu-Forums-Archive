---
title: "Return from Lock Screen...customization."
date: 2008-05-09
forum: General Help
---

### Post by Shannon_Lowder on 2008-05-09
When you first login to gnome in ubuntu, you can select one of several color schemes / themes for this screen.  But when you return from lock screen, I only get a plain white screen asking for my password.  Is there a way to make this screen use the same (or a similar) screen as the primary log on uses?

I just think this would make for a more polished looking interface.

I appreciate any heads up.

---

### Post by Zorael on 2008-05-09
Shouldn't this "white screen" have the screensaver running behind it?

Do you have any screensaver enabled?

---

### Post by Shannon_Lowder on 2008-05-09
I do have a screen saver enabled.  I'm referring to once you've gotten the screen saver to go away, and you are presented with the interface to log back in... It's all white.

Is the background supposed to continue running the screen saver, keeping the login stuff on top of that?

---

### Post by Zorael on 2008-05-09
I'm sorry, I assumed this was the case. It is in KDE, at least.

Are you using Visual Effects? If so, you could temporarily disable them and see if this white screen of yours returns to being a screensaver. Again, if this is what it's supposed to do to begin with. I'm fairly sure it shouldn't be a white screen, though.

```
$ metacity --replace &
```

---

### Post by Shannon_Lowder on 2008-05-09
You are the man!  As soon as I set visual effects to none, the screen saver, "froze" but stayed in the background as I logged back in.  Now I just need to find out what extra effect was causing it to go away.  I'll have to re-install the advanced controls for the effects, so I can turn them on one by one.

Again, thank you for the assistance!

---

### Post by Shannon_Lowder on 2008-05-09
It appears as soon as I change back to normal enhancements, or I add/change any options using compiz Config, the logon screen's background returns to white.  Could it be the case that I have a pretty logon screen OR a pretty interface?

---

### Post by Shannon_Lowder on 2008-05-12
Any ideas, Zorael?  Any way I can have both graphical enhancements to my interface, and also have the screen saver background for the return from locked screen?

---

