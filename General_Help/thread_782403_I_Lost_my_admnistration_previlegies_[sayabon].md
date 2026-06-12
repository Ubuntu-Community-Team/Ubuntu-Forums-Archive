---
title: "I Lost my admnistration previlegies [sayabon]"
date: 2008-05-04
forum: General Help
---

### Post by blacappuccino on 2008-05-04
Heys, 2 days ago i changed some settings on my ubuntu, such as: display language, other users privileges. Today when i was try to install some programs i found out that my administrator session had lost some privileges. I was to administration -> user profile editor to solve the problem but it ask me for a sabayon password... i type my password but it gives an error, and tell me to contact the administrator.

So can u explain me how i can do to found out or hack the sabayon user password, without reinstall it?

Cheers

---

### Post by tamoneya on 2008-05-04
you probably got removed from the admin group.  Boot into recovery mode by hitting D2 when GRUB loads.  This will give you root privileges.  Then user usermod to gain admin privileges.
```
usermod username -g admin
```

---

### Post by blacappuccino on 2008-05-05
Thanks for support tamoneya... i had to make some correction in the command:

sudo usermod -G admin *username*
sudo usermod -a -G admin *username*

anyway u are the man... without ur help i could never find out this.

Cheers

---

