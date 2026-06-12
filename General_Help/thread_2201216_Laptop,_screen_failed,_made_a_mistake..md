---
title: "Laptop, screen failed, made a mistake."
date: 2014-01-23
forum: General Help
---

### Post by d-william on 2014-01-23
Hello there Ubuntu Forums!

I've used a small laptop with xubuntu for quite a while now.

The screen on the laptop died, and I hooked it up to an external monitor and everything worked fine.
I accidentally deselected the monitor by clicking the "use this monitor" box though, and now my main profile won't send the screen to an external monitor.

If I log in with guest it still does, but I can't do anything from the guest profile can I?

Any easy work around for this? A simple hotkey to restore defaults? Anything.

Thanks.

---

### Post by plucky on 2014-01-23
Both my laptops use the Fn+F3 to turn on the external monitor.

I would be useful if you gave the make and model of your laptop so that any owners of the same model might be able to help you.

Good Luck

---

### Post by steeldriver on 2014-01-23
If the Fn key solution doesn't work, then if you can log in via one of the CLI virtual terminals (Ctrl-Alt-F1 etc.) you may be able to fix it from there - I *think* that the display settings are saved in a monitors.xml file so

```
mv ~/.config/monitors.xml ~/.config/monitors.xml.bak
```

may do it

---

