---
title: "Sticky notes"
date: 2015-01-24
forum: General Help
---

### Post by flex567 on 2015-01-24
Are there Sticky notes available for Xubuntu 14.04? There are pre-installed sticky notes availabe but they disappear when you reboot the system.

---

### Post by mooreted on 2015-01-24
Perhaps Tomboy Notes, it's in the software center or "sudo apt-get install tomboy".

---

### Post by Bucky Ball on 2015-01-24
*Thread moved to **General Help**.*

I use Zim. It's not quite the same as a sticky note, but certainly helps me remember things and find things easily. ;)

Just looked for 'sticky notes' in Synaptic and found knotes and rhinotes. Might be of help. There is also Clipman. Again, not exactly sticky notes, but if you copy something, you will find it in Clipman (and that includes pics).

---

### Post by flex567 on 2015-01-25
I found this [http://www.webupd8.org/2012/11/pin-notes-on-your-desktop-with.html](http://www.webupd8.org/2012/11/pin-notes-on-your-desktop-with.html)

---

### Post by Bucky Ball on 2015-01-25
> **flex567 said:**
> I found this [http://www.webupd8.org/2012/11/pin-notes-on-your-desktop-with.html](http://www.webupd8.org/2012/11/pin-notes-on-your-desktop-with.html)

Wonder if it will work in 14.**. I notice there is a .deb for 12.10 and nothing further. Is it still being developed?

---

### Post by CantankRus on 2015-01-25
> **Bucky Ball said:**
> Wonder if it will work in 14.**. I notice there is a .deb for 12.10 and nothing further. Is it still being developed?
The version doesn't appear to have changed since precise but there are builds for trusty and utopic.

You need to add the indicator plugin to the xfce4-panel if you wish to use the indicator-stickynotes menu options.
Adjust the properties of the indicator plugin for what indicators to show.
You can reload the panel after making changes with...
```
killall -SIGUSR1 xfce4-panel
```

and the command to use in startups is
```
/opt/extras.ubuntu.com/indicator-stickynotes/indicator-stickynotes.py
```

---

