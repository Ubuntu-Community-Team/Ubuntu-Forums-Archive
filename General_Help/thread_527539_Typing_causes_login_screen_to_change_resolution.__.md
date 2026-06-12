---
title: "Typing causes login screen to change resolution.  Keystrokes are otherwised ignored."
date: 2007-08-16
forum: General Help
---

### Post by donz on 2007-08-16
I have an Ubuntu system 7.04 that has been working fine:).  Today I enabled root with a password (may or may not have anything to do with problem).  Now, after rebooting, when I try to enter a user name on the login screen, the screen goes blank, my monitor shows that it is adapting to a new resolution, the screen resolution does in-fact change, but there is NO character in the Username box.  Tried F10 (as it recommended), various combinations of Ctrl-Shift-Alt-F1 (as recommended on this forum), all with the same results.  I am able to ssh into the box from other systems and login, so all is not totally lost. Hopefully someone can tell me where to look to restore the normal login functionality.

Thanks in advance

Donz

---

### Post by donz on 2007-08-16
It had nothing to do with the change of root password.  The failure was caused by adding a reference to a load library for the NX system using ldconfig.  I decided to undo everything I had done, one step at a time.  Removing the updated load library path and restoring it to the original restored the proper login behavior.  I have no idea why this interaction occurred, but it works!  :popcorn:

---

### Post by nubie177 on 2008-05-16
Same happened to me. I've done several things since last reboot.  Most recent was try to get OOo to embed mp3's, meaning java install/config.  So what exactly are the files I need to be interested in?  I'm now about to struggle with loading the install cd so I can even access the filesystem.

---

