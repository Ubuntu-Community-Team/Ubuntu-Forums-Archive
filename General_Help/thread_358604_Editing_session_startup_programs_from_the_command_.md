---
title: "Editing session startup programs from the command line?"
date: 2007-02-11
forum: General Help
---

### Post by Ach_Tee on 2007-02-11
I just installed beryl on my machine, and when I set the minimize and maximize to random it crashed. Now when I try to log in it loads up then the screen goes black. I loaded my backed up xorg.conf file but that didn't help as I think it's crashing when it tries to load the beryl-manager in the startup sessions. Is there anyway I can edit my startup programs from the command line?

---

### Post by racmar on 2007-02-11
I had a similar problem after a recent upgrade to beryl.  It was a weird problem, but it turned out to be gnome's recently used program list.  Try this and tell us if it works:

```
mv ~/.recently-used ~/.recently-used.old
```

also, you can start gnome and/or KDE in failsafe mode from the startup screen.   Use the options button in the lower left of the screen and choose "select sessions".  Then choose failsafe gnome.

---

### Post by Ach_Tee on 2007-02-11
I tried failsafe mode and it did the same thing, I'll try that command right now and see what happens.

---

### Post by Ach_Tee on 2007-02-11
OK I tried that and now instead of stopping at a black screen it loads my background. I can see it starts up conky and my menu bar, but then they just disappear.

---

### Post by racmar on 2007-02-11
what repository are you using?  I'm using:
```
# added for beryl
deb http://ubuntu.beryl-project.org/ edgy main
#deb http://beryl-mirror.lupine.me.uk/ edgy main-edgy

```

I have an intel 950 chip, what about you?  ATI? Nvidia?


Edit:  I just found this from [http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl]("http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl")
> 
I've added beryl-manager and beryl-xgl to my session startup programs, and now I can't log into my X session any more. How do I remove them again?

In case you have trouble starting up after adding beryl-manager and beryl-xgl to the GNOME session startup programs (such as getting the White Cube/blank screen after the Beryl logo) and hence can't get to the GUI to remove them, try removing the autostart entries manually:

Press Ctrl-Alt-F2 to get to a console. Log in as usual and type:

cd ~/.config/autostart
rm beryl-manager.desktop beryl-xgl.desktop



---

### Post by Ach_Tee on 2007-02-11
Awesome, thanks you just saved my day.

---

