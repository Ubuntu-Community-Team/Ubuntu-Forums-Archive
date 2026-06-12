---
title: "xterm to act as Ctrl-Alt-F1"
date: 2007-07-31
forum: General Help
---

### Post by mr4thjuly on 2007-07-31
I wan't to open the xtem that is managed with IceWM to behave in the same way as ctrl-alt-F1 i.e. I want the xterm to prompt for a password when I open it. Any ideas?
Thanks in advance.

---

### Post by kerry_s on 2007-07-31
> **mr4thjuly said:**
> I wan't to open the xtem that is managed with IceWM to behave in the same way as ctrl-alt-F1 i.e. I want the xterm to prompt for a password when I open it. Any ideas?
Thanks in advance.

are you talking sudo,root privileges? if so you would have to exec xterm with a sudo command.
Example:
xterm -e sudo ls

now if your talking about logging into a shell, in a session your already logged into, your off your rocker. the shell is already like ctrl+alt+f1 but you've already logged in, when you started X.

---

### Post by mr4thjuly on 2007-08-01
Although my xterm window does prompt me for a password now with your recommended command (xterm -e sudo ls) the xterm closes the second I type in my password. Is there a workaround to keep the window open after the password is typed in.

---

### Post by kerry_s on 2007-08-01
Why not just change your launcher to-> gksudo xterm < it will prompt for a password. 
are you sure you want to give people root privileges?

anyways, press alt+f2 & type> gksudo xterm
if that makes you happy, then right click your launcher and change the command to that.

personally i would alias "gksudo xterm" to "xterm" so they run a normal shell with no root permissions.just drop that in your ~.bashrc
alias gksudo xterm='xterm'

---

