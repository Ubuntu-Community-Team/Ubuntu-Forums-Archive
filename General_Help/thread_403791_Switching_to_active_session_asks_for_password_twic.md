---
title: "Switching to active session asks for password twice"
date: 2007-04-07
forum: General Help
---

### Post by SgtPepperKSU on 2007-04-07
If I have two users logged in to a graphical session and I try to switch from one to the other, it asks for the password twice: once to log in and once to unlock the screen.  Is there any way to get rid of the second password prompt.

What makes this particularly annoying is that I've set up pam_usb so that if my usb key is inserted that I don't have to enter a password at login, and, for some reason, it doesn't work for unlocking the screen.  If someone knows how to get that to work instead, it would be an acceptable workaround.

I'm sure that this has been asked before, but I couldn't find a suitable answer (having a separate x session and switching with ctrl-alt-F# would not pass the girlfriend-acceptance-factor).  Thanks in advance.

- Keith

---

### Post by SgtPepperKSU on 2007-04-07
Nobody else has gotten fed up with having to log in twice enough to find a solution?

---

### Post by agamonD on 2007-04-26
I'm a brand new Ubuntu (and linux for that fact) adopter, and I have to say I love it, except for this issue, which also drives me nuts.  For what it's worth, I found this problem described on the Ubuntu Launchpad site ([bug # 41333]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/41333")), which suggests to me there is nothing less advanced users can do about until they fix it there.  Also, the bug description there makes it sound like it has something to do with the "screensaver unlock dialog", but otherwise matches my experience exactly (even if I don't have the screen saver enabled).  Thoughts?

---

