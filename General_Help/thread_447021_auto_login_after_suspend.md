---
title: "auto login after suspend?"
date: 2007-05-17
forum: General Help
---

### Post by mr bob on 2007-05-17
I have auto login setup for when I start up.

But when I return from suspend to ram I always have to login. Is it possible to do anything so that I can auto login after suspend?

Nobody else uses my computer so I consider it fairly safe to auto login.

thanks.

---

### Post by strabes on 2007-05-17
I don't know if you can do this in gnome but in KDE it's quite easy to do. You simply click on the power manager icon in the notification area and the first option is a checkbox labeled "Lock screen on resume."

---

### Post by mr bob on 2007-05-18
> **strabes said:**
> I don't know if you can do this in gnome but in KDE it's quite easy to do. You simply click on the power manager icon in the notification area and the first option is a checkbox labeled "Lock screen on resume."

Thanks. I can't see a similar way in Gnome but if it is possible in KDE it should be possible in Gnome, perhaps by changing a script? Any ideas anyone?

---

### Post by defishguy on 2007-05-18
If you're using Ubuntu and the default power management setup (i.e. you're not using uswsusp or suspend2) then it's pretty easy.

Open the configuration editor by going to Application -> System Tools

If you do not see System Tools or Configuration Editor that's okay just hit Alt-F2 and type > gconf-editor

Click Apps

When the folders extend look for > gnome-power-manager

In that list you will find plenty-o-power-management goodness.  Take the check out of the box that authorizes the locking of the screen on suspend and you should be good to go.  See the attached screenshot.

---

### Post by mr bob on 2007-05-19
Yep that works. That's fantastic thanks very much.

---

