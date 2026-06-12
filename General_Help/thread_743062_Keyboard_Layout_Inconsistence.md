---
title: "Keyboard Layout Inconsistence"
date: 2008-04-02
forum: General Help
---

### Post by T21 on 2008-04-02
-Installed Hardy Heron, with en_us keyboard layout during install (cant remember if I had any other choice at the moment)

-entered my session, set keyboard layout to fr_ch, which is the actual layout of this laptop, works fine for my session.

BUT:
-keyboard layout is en_us before I login (@Ubuntu login/password GUI)

SO:
-tried editing xorg.conf, had NO impact
-tried reconfigure xserver procedure (which roughly did the same thing: change xorg.conf, correct?), had NO impact.

What am I supposed to do so that I can use consistent keyboard layout throughout utilization?

---

### Post by T21 on 2008-04-02
Can't believe such a simple question cant find a simple answer...
This keyboard layout inconstancy's just unacceptable in an end-user experience!

---

### Post by lswest on 2008-04-02
well, what you can do is go to system-->preferences-->keyboards, delete any other layouts you have there, re-make the fr_ch layout, delete the old one, and make default.  Otherwise...no real idea, that fixed it for me. (EN instead of DE)

---

### Post by T21 on 2008-04-02
> **lswest said:**
> well, what you can do is go to system-->preferences-->keyboards, delete any other layouts you have there, re-make the fr_ch layout, delete the old one, and make default.  Otherwise...no real idea, that fixed it for me. (EN instead of DE)

In this menu, it first was impossible to restore defaults, because I had edited xorg.conf. I set everything back to original values, then could reset to defaults (which of course did nothing but at least raised no exception message). I then added a "nodeadkeys" var of ch_fr kbd layout, erase original fr layout and made mine default.

No change.

Funny stuff: default Ubuntu home page begins with:
> **Ubuntu said:**
> 
Welcome to Ubuntu 8.04 LTS!

The Ubuntu project is built on the ideas enshrined in the Ubuntu philosophy: that software should be available free of charge, that software tools should be usable by people in their local language, and that people should have the freedom to customize and alter their software in whatever way they need.
So much for philosophy...

---

