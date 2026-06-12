---
title: "Stalonetray"
date: 2008-04-21
forum: General Help
---

### Post by SlalomMan on 2008-04-21
I just got rid of my panels in Gnome, mostly because I'm using AWN for most of my stuff. However, the notification applet in AWN leaves much to be desired. A post here pointed me to stalonetray, which is great, but I'd like to change some options, such as maybe making it look a little nicer and/or moving it to the corner of my screen (it's now hovering about 1/10 of the way up the screen).

I couldn't find any documentation on using it, does anyone have any pointers?

---

### Post by moonbeam on 2008-04-21
> **SlalomMan said:**
> I just got rid of my panels in Gnome, mostly because I'm using AWN for most of my stuff. However, the notification applet in AWN leaves much to be desired. A post here pointed me to stalonetray, which is great, but I'd like to change some options, such as maybe making it look a little nicer and/or moving it to the corner of my screen (it's now hovering about 1/10 of the way up the screen).

I couldn't find any documentation on using it, does anyone have any pointers?

This is my stalonetray command line.

```
stalonetray -geometry 104x48-4-4 --skip-taskbar --sticky --fuzzy-edges 3 --tint-level 10 --tint-color white -t --skip-taskbar --window-type dock --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --respect-icon-hints false --max-height 48 --icon-size 24 -i 24
```

I'm using version 0.7.6.   Some of the options I'm using are not in older versions... so if you do have an older version you will need to remove the options it doesn't like.

This places the tray in the bottom right corner of the screen and uses the pseudo-transparency feature.  It melds nicely with awn visually.

A final note:  I do patch stalonetray source to fix an old bug where awn and compiz did not recognize it as being a dock and thus showed it as an active task.   I'm not sure if this issue is still present with an unpatched stalonetray.

---

### Post by SlalomMan on 2008-04-21
Is there any way I can either:
1) make a file that will run that specific command at startup; or
2) put that into a config file for stalonetray so that it always runs with those parameters, even if I only run "stalonetray" without the extra stuff?

Thanks a lot already.

---

### Post by lotus49 on 2008-04-26
Yes there is.  You need to create a file in your home directory called .stalonetrayrc.

The stalonetray man page lists the options.

---

