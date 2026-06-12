---
title: "Can't get zsh to replace bash by default"
date: 2007-07-25
forum: General Help
---

### Post by deadlikeoscar on 2007-07-25
I recently heard about zsh and decided to try it out. I like it but I have tried using ```
chsh -s /bin/zsh myusername
``` to change the shell and it still uses bash. If I type zsh it switches to the zsh shell just fine. What am I doing wrong?

*edit* Okay so I rebooted and now it works. I figured that the change shell command would have been instantaneous but apparently not. Oh well. Glad it works now.

---

### Post by stylishpants on 2007-07-25
Probably nothing.  If your /etc/passwd file shows your username associated with zsh, then it worked. (to check: grep <username> /etc/passwd)

The thing is, if you're testing by closing your gnome-terminal and then opening a new instance, it will still use your old default shell.  This behaviour will persist until you log out of the Gnome desktop and then log back in again.

Alternatively, you can test by going to a virtual terminal and logging in there.  This should get you the new shell right away.  (Ctrl-Alt-F2 to go to the second virtual terminal, log in there, check your shell with the 'ps' command, you can return to Gnome with Ctrl-Alt-F7.)

---

