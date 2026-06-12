---
title: "Different lock screen (with a black box for password)"
date: 2017-01-12
forum: General Help
---

### Post by armansky on 2017-01-12
I am currently using Ubuntu 16.04. After locking the screen, when I try to unlock it, the lock screen shown is quite different from the usual login screen. I might have made some unwanted changes which resulted in this and I don't know which. It looks a bit Eww, as one can see in the attached image. Any probable reasons?

---

### Post by #&amp;thj^% on 2017-01-12
I do not think that is a stock login screen... have you recently made any changes to "/etc/default/grub"?
Maybe have a look there first.
```
gedit /etc/default/grub
```
Or even a custom grub due a theme maybe.
Not a lot of information to go off here to help you.

---

### Post by armansky on 2017-01-12
The login screen after logging out or after booting is the usual screen. The problem is only when the screen is locked.
I don't recall making any changes to /etc/default/grub (this is since quite some time)
Still here are my grub options:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
I reverted to the default theme and the problem still remains so I don't think that is the problem

---

### Post by #&amp;thj^% on 2017-01-12
Not sure what to add here...not knowing why this has happened...but I am sure this is user related though.
See if this is of any help: [https://askubuntu.com/questions/627431/change-lock-screen-background-through-command-line](https://askubuntu.com/questions/627431/change-lock-screen-background-through-command-line)

---

