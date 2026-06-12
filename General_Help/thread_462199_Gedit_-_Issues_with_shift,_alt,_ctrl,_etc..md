---
title: "Gedit - Issues with shift, alt, ctrl, etc."
date: 2007-06-02
forum: General Help
---

### Post by Natume on 2007-06-02
My issue is a bit odd... well, by my reckoning.  I've never had issues using gedit before, but as of today, I noticed that (it may have been due to something earlier, since I haven't used gedit for a while) it freezes on pressing the shift keys, alt keys, ctrl keys, windows key, num lock key, and menu key, though the majority of the keyboard, including tab, works just fine.

The only thing that came to mind is that maybe it changed when modifying settings for uim (I've been using it for a long while... so I doubt the program itself is the issue) or changed my keyboard layout, but I reverted both back to the simplest I could think of, and nothing's changed.  Same thing after restarting the X server and doing a reboot as well.

Any info or ponderings would be helpful.  Nano still works fine, but uh... I really do prefer gedit, and I don't feel like getting another program if I have to.  Along those lines, it should be noted that the aforementioned keys work fine in the console / terminal as well as just about every other program that I've tried.  {shrugs}

~Natume

---

### Post by Natume on 2007-06-06
Figured I'd give an update, and mention that there's no big need to respond at the moment.  I managed to bypass the problem (rather simply) by switching the input method from xim (X Input Method) to uim in gedit.  Everything appears to work fine with this change, though to be sure, I still don't know why it fails with the X input method now but didn't before my reinstallation of Ubuntu (where I still used uim).

In any case, that's that, for anybody having a similar issue after installing international language capabilities.

---

### Post by strabes on 2007-06-06
I don't know how to fix your problem but I use leafpad. It's much faster than gedit.

---

