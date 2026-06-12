---
title: "Starting lightdm without sudo"
date: 2015-04-16
forum: General Help
---

### Post by chris352 on 2015-04-16
I prefer to have my laptop boot into a terminal instead of the GUI. I can get it to work easily enough by editing the /etc/default/grub file, replacing "splash" with "text." The problem is that, when  I do want to start the GUI, it requires a total of three password entries: once to login in to tty1, once to issue the command sudo service lightdm start, and finally at the GUI login prompt. Once upon a time (before Unity), I could just login to the tty and then enter 'startx' without any further passwords required; the GUI would just start right up without the login prompt. So, two questions: a) is it possible to get 'service lightdm start' to work without sudo? b) is it possible, once logged in to tty with my user account, to go straight to GUI without the login prompt?

---

### Post by ian-weisser on 2015-04-16
> **chris352 said:**
> a) is it possible to get 'service lightdm start' to work without sudo?
Yes. Edit the /etc/sudoers file. See [the Sudoers page on the wiki]("https://help.ubuntu.com/community/Sudoers") for instructions.

> **chris352 said:**
>  b) is it possible, once logged in to tty  with my user account, to go straight to GUI without the login  prompt?
Yes. Enable autologin. See [the Autologin page on the wiki]("https://help.ubuntu.com/community/AutoLogin").

---

### Post by chris352 on 2015-04-17
Thanks for the helpful info. Unfortunately my home directory is encrypted, so I won't be able to use autologin.

---

