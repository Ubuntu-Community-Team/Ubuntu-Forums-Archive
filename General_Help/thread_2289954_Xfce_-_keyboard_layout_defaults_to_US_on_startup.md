---
title: "Xfce - keyboard layout defaults to US on startup"
date: 2015-08-08
forum: General Help
---

### Post by pickarooney on 2015-08-08
This has just started happening recently - my keyboard defaults to US each time I start the PC. I need to manually use setxkbmap gb to reset it to UK layout.
The keyboard layout in XFCE's settings have only one entry - GB - and the various .rc files I've tried to set are all GB-based as well.

I made an executable script with just one line "setxkbmap gb" in my home directory which works when run from a shell and added it to the application startup but I still end up with US layout when I log in.
So, either the autostart is being ignored or else something else is overwriting the script after it's run.

Is there somewhere else I could add the command to ensure that it's the last thing run on startup?

---

### Post by Vladlenin5000 on 2015-08-08
Perhaps you should remove the default US keyboard if you don't need it.

---

### Post by pickarooney on 2015-08-10
I don't have a default US keyboard anywhere (that I know of)

---

### Post by Bashing-om on 2015-08-10
pickarooney; Hello;

Maybe as simple as having the system re-configure the keyboard identification ?
```

sudo dpkg-reconfigure keyboard-configuration

```
Which will start an interactive wizard to set the keyboard environment .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by pickarooney on 2015-08-20
After trying everything I could think of, the issue disappeared after updating to ubuntu 14.10. Strange

---

### Post by Bashing-om on 2015-08-20
pickarooney; Welp, 


Good news.
That is a step in the right direction, but need to keep on step'n.
Release 14.10 is End_Of_Life and is no longer supported. Step on up to 15.04 (EOL Jan).
Will get a Long Term Support Release (16.04) in April of 2016 .

[INDENT][INDENT]newer can be better
[/INDENT][/INDENT]

---

