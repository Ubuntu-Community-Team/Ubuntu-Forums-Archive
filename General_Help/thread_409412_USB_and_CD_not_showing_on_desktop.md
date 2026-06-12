---
title: "USB and CD not showing on desktop"
date: 2007-04-14
forum: General Help
---

### Post by floke on 2007-04-14
Ok so this is not a major issue but has been bugging me slightly for a while.
Some time ago during an upgrade to Feisty all of my mounted drives started to appear on my desktop. Clearly I could unmount them - but can't unmount the drive I'm actually using so am stuck with it. Using gconf-editor (apps-nautilus-desktop) I can uncheck volumes displayed and make them all disappear but then - and this is the pain - my USB, external HDD, CDs and DVDs fail to show on the desktop when mounted.

Is there any way around this? I know it's possible since this is how it used to be.

---

### Post by floke on 2007-04-15
Anyone?

---

### Post by floke on 2007-04-17
I know that someone knows.....

---

### Post by firebadger on 2007-04-17
Run gconf-editor from the command line.  It's somewhere in there.

---

### Post by floke on 2007-04-17
> **firebadger said:**
> Run gconf-editor from the command line.  It's somewhere in there.

Please read first post in the thread. Been there. Tried that. Done it. Doesn't work.

---

### Post by floke on 2007-04-23
Problem solved.
Unmount visible drives on desktop manually, and, since I don't need access to them from Feisty - comment them out in fstab.

Too simple I avoided the obvious solution!

---

