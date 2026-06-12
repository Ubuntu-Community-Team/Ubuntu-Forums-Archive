---
title: "First it says I can upgrade, then I can't"
date: 2013-06-08
forum: General Help
---

### Post by pmatos on 2013-06-08
Look at this:
```
 $ ssh pmatos@jupiter
pmatos@jupiter's password: 
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Fri May 31 20:45:53 2013 from mercury.local
pmatos@jupiter:~$ sudo do-release-upgrade
[sudo] password for pmatos: 
Checking for a new Ubuntu release
No new release found

```
Suggestions are welcome.

---

### Post by 2F4U on 2013-06-08
Seems as if you are already running 13.04, or am I missing something?

---

### Post by Impavidus on 2013-06-08
Try this:
[http://askubuntu.com/questions/287939/update-available-message-after-installing-update](http://askubuntu.com/questions/287939/update-available-message-after-installing-update)

---

### Post by pmatos on 2013-06-21
> **Impavidus said:**
> Try this:
[http://askubuntu.com/questions/287939/update-available-message-after-installing-update](http://askubuntu.com/questions/287939/update-available-message-after-installing-update)

That worked, thanks.

---

