---
title: "Gnome-keyring fills my auth.log"
date: 2020-07-04
forum: General Help
---

### Post by burkina76 on 2020-07-04
Hi all,

my root partition on Ubuntu 18.04 suddenly became completely full,  because of a huge /var/log/auth.log (>300 Gb). Indeed, the following  entry:

```
gnome-keyring-daemon[2466]: couldn't accept new control request: Too many open files
```

repeats several times each second!
I cleaned the log (with ```
 >/var/log/auth.log 
```), but I would like to understand what's going on and resolve it,  since it will fill it again. To be honest, I don't know if I really use  gnome-keyring or not.
It may be useful to know that I cannot physically access the PC now, so I  use it remotely via vnc (will the ssh authentication pass via the  keyring?). For the same reason, I do not dare rebooting it...

Thanks!
Stefano

---

### Post by dino99 on 2020-07-04
Start cleaning the system via bleachbit (as root, carefully select options)

---

### Post by burkina76 on 2020-07-08
Hi all,

I solved the issue, at least for the moment, since I haven't understood the real origin.
In any case, I stopped the vnc and killed gnome-keyring-daemon.
Then I restarted the vnc and connected with Remmina: at this point gnome-keyring asked me for my password (so indeed it is linked to the vnc connection).
Now everything works as usual, and the log is not filled by that error message.

Stefano

---

