---
title: "gksudo broken first try but second works"
date: 2008-02-22
forum: General Help
---

### Post by funky_munky on 2008-02-22
Hi it seems as though I have broken gksudo on my laptop but not sure how.  If I use gksudo from a menu item that requires it or from a terminal the first time (assuming time has passed since it was last used) nothing happens as in no password prompt and program fails to continue.  If I try it again after it fails then it opens the password prompt like normal.  I found that gksudo (from the man pages) has a debug and so I tried it there. gksudo -d gnome-text-editor after the password has expired in memory gives me this
```
 gksudo -d gnome-text-editor
No ask_pass set, using default!
xauth: /tmp/libgksu-iM4gIi/.Xauthority
STARTUP_ID: gksudo/gnome-text-editor/1634-0-cair-paravel_TIME1108189760
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gnome-text-editor
buffer: -Password or swipe finger:                                                                                                                                                                                                                                      -
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

```

This is all that happens.  No password box and no text editor opening.  Any help would be much appreciated.

Second attempt works like this:
```

 gksudo -d gnome-text-editor
No ask_pass set, using default!
xauth: /tmp/libgksu-yxwNCH/.Xauthority
STARTUP_ID: gksudo/gnome-text-editor/2112-0-cair-paravel_TIME1110597640
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gnome-text-editor
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-yxwNCH/.Xauthority
xauth_env: /home/jamey/.Xauthority
dir: /tmp/libgksu-yxwNCH

```

password box comes up and upon successful entering the text editor opens

---

### Post by dgruetter on 2008-05-06
The same thing is happening here. I always get it saying "starting administration" and then it disappears. I used to get the password prompt after a few tries but not I cannot get any prompt even after several attempts.

---

### Post by funky_munky on 2008-05-06
I forgot about this thread.  I found that the problem was that I had set up my computer to be able to use pam with my fingerprint scanner on my laptop to login.  For some reason there is no prompt but swiping my finger is acknowledged.

---

