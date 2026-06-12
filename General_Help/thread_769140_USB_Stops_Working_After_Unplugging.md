---
title: "USB Stops Working After Unplugging"
date: 2008-04-26
forum: General Help
---

### Post by Vaelrith on 2008-04-26
After I unplug anything from USB, I can no longer plug anything else in and get it to work without restarting the computer.  For example, if I plug in an external hard drive into the USB slot, then unplug it, I have to restart my computer in order to plug anything else into any USB slots.

Thanks

---

### Post by Vaelrith on 2008-04-27
Bump?

---

### Post by ghost_ryder35 on 2008-04-27
are you "Ejecting" them?

---

### Post by Vaelrith on 2008-04-27
If it's something like a webcam or wireless mouse I can't eject it.

---

### Post by ghost_ryder35 on 2008-04-27
true.  Maybe a problem with HAL.... GRRR....  brb, google time :)

---

### Post by Vaelrith on 2008-04-27
Hmm.  It was like this in Gutsy but I just lived with it, but it's started to get really annoying.

---

### Post by Vaelrith on 2008-04-28
bump?

---

### Post by retrow on 2008-04-28
[note]Not an expert advice[/note]

See if this helps. Open configuration editor by typing in gconf-editor in the terminal.

Then apps > Nautilus > Preferences

Check if you have media_automount and media_automount_open options checked.

[img]http://nuclear-imaging.info/files/image/gconfautomount.png[/img]

---

### Post by Vaelrith on 2008-04-28
Yes, they are both checked.

---

### Post by retrow on 2008-04-28
My so called 'expertise' on that matter ends there :(

---

### Post by Vaelrith on 2008-04-28
Ah, well thanks for trying retrow.

---

