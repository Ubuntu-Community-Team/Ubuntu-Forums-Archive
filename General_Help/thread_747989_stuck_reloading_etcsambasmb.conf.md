---
title: "stuck reloading /etc/samba/smb.conf"
date: 2008-04-07
forum: General Help
---

### Post by eidam655 on 2008-04-07
hello,

i have a problem (heh, surprise :)).

recently, i have changed something in the loading sequence of modules. i'll be honest, i do not remember what it was; i continued working after the changes several hours. today, when i tried to boot linux, i got stuck on a message 'Reloading drivers /etc/samba/smb.conf' and does not go on.

if anyone does know how can this problem be solved, thank you in advance for your reply :)

i attach my smb.conf file and the log files from the boot.

---

### Post by Beefeater on 2008-04-07
Try and bind it to an interface by adding for example

```
interfaces = eth0
```

to your smb.conf

---

