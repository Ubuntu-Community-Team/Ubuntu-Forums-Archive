---
title: "running an sshfs command at start up"
date: 2007-05-13
forum: General Help
---

### Post by ffxr on 2007-05-13
hi, i use this command to mount a remote folder locally

```
sshfs mythtv@192.168.1.20:/video /home/fxr/mythtv-files/
```

i want it to be auto mounted on start up.. i know i can make a script & get that to run at start up, but how do i pass the password to the command?

can anyone assist?

---

### Post by kidders on 2007-05-14
Hi there,

The "right" way to do this is probably in /etc/fstab, although I did a little poking and discovered Ubuntu seems to be missing the part of fuse-utils that makes that possible. You might be interested in [http://www.john-hunt.com/linux/2006/10/30/fixing-fuse-for-auto-mounting-in-your-fstab-via-sshfs/](http://www.john-hunt.com/linux/2006/10/30/fixing-fuse-for-auto-mounting-in-your-fstab-via-sshfs/).

> **ffxr said:**
> i know i can make a script & get that to run at start up, but how do i pass the password to the command?Yep... that's the other way of going about it. I'd say using key-based authentication (rather than password authentication) would be a safe & convenient way of avoiding having to interact with the **sshfs** command. You *can* get a script to mess around with stdin and stdout if you really want to, but avoiding it altogether would probably just be easier.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

