---
title: "scambled display, terminal terminates; complete lockout"
date: 2007-12-06
forum: General Help
---

### Post by MartijnBuijs on 2007-12-06
I installed Xubuntu 7.10 Alt on an older machine. The display does not support the 1024x768 @ 70Hz which it boots into (max is 60Hz), and the result is a unreadable scrambled screen. I have to temporarily switch the monitor with another one, select lower refresh rate, and then switch monitors again in order to be able to access anything.

I read one can edit the xorg.conf file to change the refresh rate range. What I've learned so far is that in order to have access to the file, I supposedly need to go into terminal (sudo etc.).

But the terminal switches back to the login screen in after a few seconds, and starts a new session. I have read this may have to do with the display bit depth (changing 24 to 16) in the xorg.conf file, but of course I cannot access that! Chicken, egg etc.

How do I go about solving this?


BTW, Isn't there a way to type commands in a fancy windowed terminal (i.e. like Windows dos prompt)? I'm also getting tired of typing in passwords for every change I make...

---

### Post by pointone on 2007-12-06
Press Ctrl+Alt+F1 to access a terminal. Press Ctrl+Alt+F7 to return to X.

You can try booting into recovery mode (from the GRUB boot menu) which will prevent X from loading if this is causing you problems.

---

### Post by MartijnBuijs on 2007-12-07
Ok, I booted into recovery mode, and edited xorg.conf with vi, tried all sorts of refresh ranges, including 60-60 in an attempt to explicitly force 60Hz (monitor supports 50-60Hz), but no luck at all.

Also, I'm not sure what the horizontal refresh rate setting does, changing it didn't seem to have any impact.

1024x768 @ 60Hz is definitely supported by the monitor, and works if I switch monitor, lower to 60Hz and switch back. This setting seems to be discarded on reboot, can I fix this?

Or is there a way I can force X to a lower resolution (800x600 would be fine)? Perhaps that might work?

---

### Post by MartijnBuijs on 2007-12-08
Bump. :)

---

### Post by MartijnBuijs on 2007-12-10
Simple question: how do I configure a fixed resolution that is remembered each time it boots?

There's got to be a better way than switching hardware right? :confused:

---

### Post by MartijnBuijs on 2007-12-11
Is this thing on?

---

