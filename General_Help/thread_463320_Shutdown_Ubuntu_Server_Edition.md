---
title: "Shutdown Ubuntu Server Edition"
date: 2007-06-03
forum: General Help
---

### Post by JulianRoot on 2007-06-03
Hello,

I have installed the Ubuntu Sever Edition. If I run "sudo shutdown now" on the system, it switches into the maintenance mode as root. How can I do a soft shutdow instead of a hard one?

Julian

---

### Post by Ek0nomik on 2007-06-03
```
sudo shutdown -r now
```

should restart the computer.

---

### Post by JulianRoot on 2007-06-03
And how to shutdown it? I don't want to reboot it.
Or aren't you allowed to switch off a server?

---

### Post by steeleyuk on 2007-06-03
List of shutdown commands (taken from Wikipedia)

```
usage:  shutdown [-akrhfnc] [-t secs] time [message]
    -a        use /etc/shutdown.allow
    -k        don't really shutdown, only warn
    -r        reboot after shutdown
    -h        halt after shutdown
    -f        do a 'fast' reboot (skip fsck)
    -F        force fsck on reboot
    -n        do not go through "init" but go down real fast
    -c        cancel a running shutdown
    -t secs   delay between warning and kill signal
```

Any of those any use?

---

### Post by JulianRoot on 2007-06-03
Maybe it's "-h". I can't try it now. I'll tell you if it works...

---

