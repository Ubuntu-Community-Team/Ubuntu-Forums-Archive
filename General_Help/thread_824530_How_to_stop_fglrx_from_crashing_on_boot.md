---
title: "How to stop fglrx from crashing on boot"
date: 2008-06-10
forum: General Help
---

### Post by Simplechat on 2008-06-10
I have a 8.04 box with a X1950 pro graphics card that has been running with the fglrx driver since 7.04.

The problem is that apparently, since lunchtime today, something has been updated meaning that on login, after a second or so, the monitor turns black and the computer becomes unresponcive (numlock/etc buttons don't move, fans spin up, and nothing much happens afterwords).

To be specific, this started after i used the update manager to update. After a few hours my computer froze (unresponcive, reboot), then it started its main symptom.

I managed to fix it by changing x.org to use the vesa driver instead, but i want to reenable fglrx in the near future (games & desktop effects), and i'm wondering how i would go about doing that in a manner that doesn't cause instantaneous crashing.

has anyone else had this problem?

---

### Post by destructaball on 2008-06-10
Turn on your computer and press Ctrl-Alt-Backspace does this take you to your login page?

---

### Post by Simplechat on 2008-06-10
> **destructaball said:**
> Turn on your computer and press Ctrl-Alt-Backspace does this take you to your login page?

No, computer is completely unresponcive. Num lock/caps lock lights don't change when you hit the keys, etc. (something dies HARD)

Further, i installed the latest fglrx from ATI ([http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)), and tried reenabling, same problem.

---

