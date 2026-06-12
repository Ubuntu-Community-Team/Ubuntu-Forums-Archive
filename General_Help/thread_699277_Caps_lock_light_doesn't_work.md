---
title: "Caps lock light doesn't work"
date: 2008-02-17
forum: General Help
---

### Post by sammydee on 2008-02-17
Hi all

Recently in ubuntu gutsy the caps lock light stopped turning on and off with the caps lock key. It works in windows, and used to work in ubuntu, not sure what has changed.

Any help?

Sam

---

### Post by mojoman on 2008-02-17
> **sammydee said:**
> Hi all

Recently in ubuntu gutsy the caps lock light stopped turning on and off with the caps lock key. It works in windows, and used to work in ubuntu, not sure what has changed.

Any help?

Sam

I've also noticed this and I too would be interested in a fix. It used to work in Feisty but doesn't work in Gutsy. I'm using a run-of-the-mill Logitech media keyboard, nothing fancy. Doesn't work in Debian Lenny either.

---

### Post by Flyingjester on 2008-02-17
you might want to file a bug report with launchpad.

---

### Post by shadowhywind on 2008-03-16
does anyone have a solution to this yet, I just ran into this issue today. Thanks

---

### Post by shadowhywind on 2008-03-17
I just solved my issue, hopefully this solution might help someone else. 

uninstall the mouseemu package, and reboot. It solved the LED issue for me. 

Enjoy

---

### Post by klange on 2008-03-22
> **shadowhywind said:**
> I just solved my issue, hopefully this solution might help someone else. 

uninstall the mouseemu package, and reboot. It solved the LED issue for me. 

Enjoy

I can confirm this. It also fixed my num lock operation (and light).

---

