---
title: "Unable to login to ubuntu16.04LTS"
date: 2017-03-03
forum: General Help
---

### Post by emcquinn8 on 2017-03-03
I have rebooted numerous times and keep getting stuck at the login screen. Cannot login as a guest either. Have password disabled.

---

### Post by dragonfly41 on 2017-03-03
It could be that it is something simple .. like having your keyboard Caps Lock on, or a key in keyboard stuck.

If that is not the case follow password recovery guides such as here ...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by emcquinn8 on 2017-03-03
It's not the caps lock. My computer does not require a password. You just have to select login and that should bring u to desktop. But on my computer it's not doing that it keeps bringing me back to the login screen.

---

### Post by dragonfly41 on 2017-03-03
I would hazard a guess that you will need to bootup Live Ubuntu USB/CD
then access [COLOR=#111111][FONT=Ubuntu]/etc/sudoers .. which is dangerous if you read about it.

Since I haven't done that myself I advise that you search this forum further
to restore a user password and get to the point where you can login after reboot.

And at the very least backup /etc/sudoers in case you corrupt the file.

this is what my sudoers file contains

[/FONT][/COLOR]```
# User privilege specification
root    ALL=(ALL:ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

```

Reading around, when the password is disabled the %admin line reads

```
[COLOR=#000000]%admin ALL=(ALL) NOPASSWD: ALL
```[/COLOR]
[COLOR=#111111][FONT=Ubuntu]


[/FONT][/COLOR]

---

### Post by emcquinn8 on 2017-03-03
Hi df why has this issue arisen on my ubuntu

---

