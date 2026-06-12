---
title: "Change screen locking mechanism"
date: 2013-03-10
forum: General Help
---

### Post by Stonecold1995 on 2013-03-10
Is there a way to change what is run to lock the screen in KDE?  Currently this is what's run by krunner:```
/usr/lib/kde4/libexec/kscreenlocker --forcelock
```I'd like to be able to change it so that when I close the screen (or to Control+Alt+L, or Kickoff>Leave>Lock), instead this is run (as root):```
/usr/bin/vlock --new --disable-sysrq
```That way, if I accidentally leave open a different tty when I lock the screen, everything will be locked, instead of just the tty that the X server is running in.  Plus it'll allow me to run other commands at screen lock, so I can do things like dismount encrypted TC volumes with sensitive documents and close the KDEWallet, etc.Is there any way to do this?

---

### Post by Stonecold1995 on 2013-03-24
bump

---

