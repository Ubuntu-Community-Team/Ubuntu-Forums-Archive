---
title: "What other commands, besides Ctrl + Alt + Backspace, restart things?"
date: 2008-01-30
forum: General Help
---

### Post by rainwalker on 2008-01-30
Sometimes Compiz Fusion will totally freeze everything and I can't restart X via Ctrl + Alt + Backspace. I don't know if it's because my keyboard freezes or if something (maybe X itself) crashes and won't respond to it.
Are there any other commands/methods to restart things (I'm not exactly sure what) when Compiz freezes? I REALLY don't like doing a hard shutdown

---

### Post by jan quark on 2008-01-30
try this one

alt+print+K

it will log out and you are in the login screen

---

### Post by Shazaam on 2008-01-30
control+alt+printscreen (SysrRq). While holding these keys down type in reisub. This will gracefully shutdown your system.
From the SysRq wiki....

"Raising Elephants

To perform a safe reboot of a Linux computer which has otherwise locked up, the mnemonic "Raising Elephants Is So Utterly Boring", or simply remembering the word "BUSIER" backwards, is often useful. It stands for Raw (take control of keyboard back from X), tErminate (kill -15 programs, allowing them to terminate gracefully), kIll (kill -9 unterminated programs), Sync (flush data to disk), Unmount (remount everything read-only), reBoot. These keystrokes should be entered a few seconds apart. This should prevent a fsck being required on reboot; it also gives some programs a chance to save emergency backups of unsaved work."

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by dcstar on 2008-01-30
> **rainwalker said:**
> Sometimes Compiz Fusion will totally freeze everything and I can't restart X via Ctrl + Alt + Backspace. I don't know if it's because my keyboard freezes or if something (maybe X itself) crashes and won't respond to it.
Are there any other commands/methods to restart things (I'm not exactly sure what) when Compiz freezes? I REALLY don't like doing a hard shutdown

Usually toggling something like the "Num Lock" key will show you if the keyboard is still active, if it isn't then you may be totally stuffed.

If the keyboard still functions, then CTRL-ALT-F1 should give you a text login screen, and when you login you can do this to restart your X session:

```
sudo /etc/init.d/gdm restart
```

Pressing the Power button on a modern PC once (usually) kicks of the Shutdown process, you should try this and allow Ubuntu time to complete the shutdown properly.

---

### Post by rainwalker on 2008-01-30
> **dcstar said:**
> Pressing the Power button on a modern PC once (usually) kicks of the Shutdown process, you should try this and allow Ubuntu time to complete the shutdown properly.

I'm on a laptop, and I have it set to ask me what to do when I push the power button so that doesn't work

Thanks everyone for your help :)
Now I'll just have to remember all this next time it freezes...

---

### Post by dcstar on 2008-01-31
> **rainwalker said:**
> I'm on a laptop, and I have it set to ask me what to do when I push the power button so that doesn't work


In Gnome, System-Preferences-Power Management-General has a setting for these things.

---

### Post by rainwalker on 2008-01-31
> **dcstar said:**
> In Gnome, System-Preferences-Power Management-General has a setting for these things.

That's actually what I like it to do, though...

---

