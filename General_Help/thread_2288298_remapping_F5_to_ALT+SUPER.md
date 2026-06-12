---
title: "remapping F5 to ALT+SUPER"
date: 2015-07-25
forum: General Help
---

### Post by leeko on 2015-07-25
Hi,

I'd like to remap my F5 key (actually "switch windows" on a chromebook keyboard) to the key combination "left ALT + SUPER" so that when I press "left ALT + SUPER", it does the same thing as pressing the F5 key. The keycode for F5 is 63. 

I thought I could use xsendkeys, but it looks like that's no longer available on ubuntu 14.04. I looked at the man for xkb, but that's a bit above my level of understanding. 

Can anyone help me figure out how to do this? I'm running xfce on Ubuntu 14.04LTS via a chroot (crouton) on ChromeOS.

Thanks,

Lee

---

### Post by Bucky Ball on 2015-07-26
Xfce? Settings> Keyboard> Application Shortcuts is how you set up a key combo. Unsure how you would set up the F5 key, though. Setting up Alt+Super is easy.

You would be better off probably looking for the command that switches window (rather than the F5 key) and using that as the command for the shortcut. In Application Shortcuts, do you see F5 being used already for what you are saying? If so, change the key to alt+super.

---

