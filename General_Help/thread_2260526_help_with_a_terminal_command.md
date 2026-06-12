---
title: "help with a terminal command"
date: 2015-01-12
forum: General Help
---

### Post by nep-nori on 2015-01-12
I need someone savvy to confirm wether or not

```
sudo sh -c 'printf "[SeatDefaults]\ngreeter-hide-users=true\n" >/usr/share/lightdm/lightdm.conf.d/50-no-userlist.conf'

```

will hide the userlist on lightdm's login screen, and wether or not

```
sudo sh -c 'printf "[SeatDefaults]\ngreeter-show-manual-login=true\n" >/usr/share/lightdm/lightdm.conf.d/50-manual-login.conf'

```

will allow me to type my user and pass manually. These are modified commands found right here in the forums but the original ones (which I've already used) were for disabling and hiding the guest and remote account options respectively.

---

### Post by TheFu on 2015-01-12
This will overwrite any existing file that may be in the location. It almost always isn't an issue, but it could be on some systems.
I would check whether this file exists, and if so, exit .... or just add the lin you want as a comment to the end.

The way above is interesting. I'd have just created the 2 files I wanted, inside a full directory structure with appropriate permissions, owner/group and scp'd them into place or used Ansible to do it if I had more than 10 machines. Ansible isn't really useful for people at home. It is a DevOps tool.  A single line can fail for lots of reasons - what happens if the directory doesn't already exist? It will fail.

Sorry - cannot say definitively what those settings do or do not do related to login screens.  But I thought lightdm settings belonged under /etc/lightdm/lightdm.conf.d/ . That's where I've got my custom setup to remove the userid picklist.

/etc/lightdm/lightdm.conf.d$ more 50-custom-config.conf  my file:
```
[SeatDefaults]
greeter-hide-users=true
greeter-show-manual-login=true
allow-guest=false

```

---

