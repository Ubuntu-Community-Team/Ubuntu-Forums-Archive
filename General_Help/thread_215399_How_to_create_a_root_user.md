---
title: "How to create a root user"
date: 2006-07-13
forum: General Help
---

### Post by Tayeb on 2006-07-13
Hi guys,
I sort of deleted my original user, the one I installed with, and now I can't access [COLOR="Red"]Synaptic[/COLOR], the message I get is
[I]Not runing as root
The application will run in read-only mode. You will not be able to change the package database.[/I]
when I enter the command [COLOR="Red"]gksudo gedit[/COLOR], I get the following error message:
[I]Failed to run gedit
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I]
even when  I enter my password.
I don't know what to do.
Thanks

---

### Post by scxtt on 2006-07-13
so how are you logged in if your account is "sort of deleted"? ...

you can boot into recovery mode and as root, do a **useradd {new user name}; passwd (new user name)** to create a new account - then, as root, do a visudo and add the new username to the sudo list ...

---

### Post by taurus on 2006-07-13
If you happen to delete the original user, then how did you log in?  If you can't log in as all because there is no user on your system, then you need to boot it into recovery mode (from GRUB menu).  Then, at the prompt/console, do

```

useradd -m -G adm,admin,audio,audio,cdrom,games -s /bin/bash <username>
passwd <username>

```
Reboot and you are back in business...

---

### Post by aysiu on 2006-07-14
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

