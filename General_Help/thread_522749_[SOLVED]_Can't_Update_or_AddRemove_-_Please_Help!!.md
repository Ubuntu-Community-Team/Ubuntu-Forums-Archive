---
title: "[SOLVED] Can't Update or Add/Remove - Please Help!!"
date: 2007-08-11
forum: General Help
---

### Post by g3rik on 2007-08-11
I'm currently running Fiesty Fawn on an IBM 600E laptop.  I have upgraded from Dapper to Edgy and then from Edgy to Fiesty.  I updated using the gksu "update-manager 'c" command.  However, now when I try to add an app/game using the add/remove option, Fiesty starts the process but will not finish.  It just quits and nothing gets installed.  The same thing happens when I try to install the latest software updates.  I'm not sure how to fix this.  Someone please help, as I am a newbie to this great operating system.  Thanks!

---

### Post by aysiu on 2007-08-11
I have no idea what might be wrong, but you might want to try two things:

1. Can you update through the terminal? ```
sudo apt-get update && sudo apt-get dist-upgrade
```

2. Try running Add/Remove from the terminal and seeing if any error messages spew out: ```
gksudo gnome-app-install
```

---

### Post by g3rik on 2007-08-11
Aysiu, thanks for your reply.  I tried what you said. and got the following error message in terminal:

When I tried this:  sudo apt-get update && sudo apt-get dist-upgrade
I got this error:  sudo: /etc/sudoers is owned by uid 1000, should be 0

When I tried this:  gksudo gnome-app-install
I got no error message, but absolutely nothing happens.  Terminal just shows me the next command line.

Any ideas now??

---

### Post by aysiu on 2007-08-11
Reboot.

Select **Recovery mode**

Type ```
chown root:root /etc/sudoers
reboot
``` Select the normal boot mode.

---

### Post by g3rik on 2007-08-11
Wow, that did it!  Performing software updates right now.  Thank you very much!!

---

