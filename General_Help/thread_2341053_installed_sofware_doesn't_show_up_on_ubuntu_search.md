---
title: "installed sofware doesn't show up on ubuntu search"
date: 2016-10-24
forum: General Help
---

### Post by William_Labbett on 2016-10-24
Hi,

Need some help again.

 I'm using ubuntu 12.04. I've installed brasero (sudo apt-get install brasero).

When I use the search ubuntu button at the top of the launcher on the left hand side of the Desktop it doesn't show up like all the other
programs.

Is there something I need to do to get brasero put within search's sight??

---

### Post by RobGoss on 2016-10-24
Have you tried rebooting your machine sometime the system may need to restart in order to see any new software in some cases

Second, make sure you're running the correct command be weary of typos. You may also want to see if that software is actually installed

Usually Ubuntu systems let you know when the installation is complete and allows you to launch any new applications that was installed depending on how it was installed

---

### Post by howefield on 2016-10-24
Brasero should be installed by default in 12.04 ?

```
apt-cache policy brasero
```

will tell you if in fact it is installed.

---

### Post by fenrice on 2016-10-24
did you type brasero at the command line? Also "dpkg -s <package>" is a good way to search too

---

