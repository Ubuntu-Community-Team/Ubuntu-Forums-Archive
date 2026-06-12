---
title: "Gutsy Completely Freezes... What Do I Do?"
date: 2008-01-06
forum: General Help
---

### Post by djrobthaman on 2008-01-06
Hi there, 

I've noticed that every once in a while gutsy will become completely unresponsive.  I can move the mouse around but no matter where I click nothing responds.  It doesn't respond to keyboard commands either.  But, if I had a text editor focused at the time, the cursor will still be flashing.  The music I'm listening to in amarok will continue to play and even go on to the next track.

Even after all of this said... I can actually restart the session by hitting ctrl+alt+backspace.

Has anyone experienced this and know what it could be or how I could figure out what my problem is?

Thanks

---

### Post by colo on 2008-01-07
Every tried switching to another VT (Ctrl+Alt+F1), checking the output of the following commands?:

```

dmesg | tail
tail .xsession-errors
tail /var/log/Xorg.0.log

```

Maybe that gives you some hints on what is going awry.

---

### Post by rune0077 on 2008-01-07
Try adding a system-monitor to the panel to monitor CPU-usage. If music keeps playing and programs stay active, it may be because you're using all your processing power.

---

### Post by philinux on 2008-01-07
Could be trackerd. Its' been known to slow things down while indexing. Is your HD light on when its freezing?

Check using top from a terminal.

System>Prefs>Indexing preferences.

---

### Post by djrobthaman on 2008-01-08
Hi everyone,

Gutsy froze again and so I tried what colo recommended and got a whopper of a message output.  I really don't know how to look through and figure out what might be the culprit.  If anyone could take a look and see what they think I would really appreciate it.


Thanks so much

PS I've attached the file (tried to put it in the message but ubuntuforums thought I was uploading 50 photos... yeah it's that big :) )

---

### Post by djrobthaman on 2008-01-08
Woops, didn't realize there was an error when I uploaded it (again too big).  Zipped it now and it should be ok.

---

