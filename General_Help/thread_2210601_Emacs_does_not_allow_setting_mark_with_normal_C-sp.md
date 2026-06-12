---
title: "Emacs does not allow setting mark with normal C-space"
date: 2014-03-11
forum: General Help
---

### Post by cpbl on 2014-03-11
Normally in Emacs you set the mark with Ctrl-space.  This isn't working under Emacs in 14.04.
Ctrl-@ still works.  
Is this a bug?

---

### Post by PaulW2U on 2014-03-12
> **cpbl said:**
> Normally in Emacs you set the mark with Ctrl-space.  This isn't working under Emacs in 14.04.
Ctrl-@ still works.  
Is this a bug?

I've tried both Emacs23 and Emacs24 in **K**ubuntu 14.04 and Ctrl-Space sets a mark.

May be Ubuntu is not passing that key combination onto Emacs and is using it for something else? Sorry, I don't have an Ubuntu installation available at present.

**Edit**: This bug report describes your problem: [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1278569](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1278569)

---

### Post by cpbl on 2014-03-12
@PaulW2U -- Thanks! for the report and link. No need for me to submit one then.

---

### Post by SeijiSensei on 2014-03-12
You can give [jed]("http://www.jedsoft.org/jed") a try as an Emacs replacement.  It's in the repositories.  I've used jed for years having grown up on Emacs once long ago.

---

### Post by christo3 on 2014-05-18
I had the same problem. I use Kubuntu . There's the IBUS preference settings icon on the system tray. One of the Keyboard shortcuts is using C-SPC. I clear this and the shortcut now works in Emacs again.:P

---

### Post by cariboo on 2014-05-18
Moved to General Help, as this has nothing to do with Utopic.

---

### Post by hawkeye2 on 2014-05-29
Thank you!

---

### Post by el3ctron on 2014-10-30
run ibus-setup and reconfigure the hot key, it works for me!

---

