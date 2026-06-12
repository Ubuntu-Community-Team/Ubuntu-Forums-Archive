---
title: "I made a noob mistake- how can I get my Admin rights back?"
date: 2013-06-24
forum: General Help
---

### Post by Knucklehead401 on 2013-06-24
Any help is very much appreciated. I thought I needed to change my Admin account to a regular account because I thought the Admin account was the same as the root account. I learned differently but had already changed my Admin account to regular. Ubuntu 12.4 states that I must have the root password to make the change back but I don't know my root password. It is not the same as my Admin account password and I have tried very password I can think of to no avail.  Is there any way I can get my Admin privileges back without an unistall & reinstall of Ubuntu?  Or will it really matter if I can still sudo commands when I need to install packages, etc? Thanks any help. I really want to avoid an uninstall & rreinstall if possible.

Knucklehard10652
An Ubuntu noobie

---

### Post by TylerD75 on 2013-06-25
Try single user mode.  Here's a step by step guide: [Grub Single Usermode]("http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/").
Once you're in, just set a new password with the passwd command.

---

### Post by HiImTye on 2013-06-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
log into recovery mode by restarting and choosing it at the menu before Ubuntu loads, then add your user to the groups adm and sudo```
usermod -a -G adm,sudo <user>
```you may need to remount your drive writable by finding it with```
df -h
```it will be mounted at / such as mine```
[ tye@T: ~ ]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4        99G   14G   80G  15% /
udev            1.6G  4.0K  1.6G   1% /dev
tmpfs           628M  1.7M  626M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.6G  4.0K  1.6G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
cgroup          1.6G     0  1.6G   0% /sys/fs/cgroup
/dev/sda3       1.7T  1.1T  574G  66% /storage
```mine is this one```
/dev/sda4        99G   14G   80G  15% /
```so I would remount it rw```
mount -o rw,remount /dev/sda4
```

---

### Post by Knucklehead401 on 2013-06-27
I will try this. Thank you very TylerD much for your help.

---

### Post by Knucklehead401 on 2013-06-27
Thank you HiImTye. Very nice step-by-step is what this noob needs.

---

### Post by HiImTye on 2013-06-28
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you're welcome :D
let me know if you have any problems, and if not, mark it solved so someone else can benefit by: editing the first post, choosing 'go advanced,' then changing 'prefix' from [Ubuntu] to [SOLVED]

---

### Post by steeldriver on 2013-06-28
just an fyi, there's no need to manually look up the block device (e.g. /dev/sda4) - you can just tell remount via the current mount point (i.e. /)

```
mount -o rw,remount **/**
```

---

### Post by mastablasta on 2013-06-28
and another fyi: sudo  comes from "super user do" and then you continue with whatever the *super user *wants to do. :-) so it's not root account and not admin account but a super user account. 
> Unlike the su command, users typically supply their own password to sudo. After authentication, and if the configuration file permits the user access, then the system will invoke the requested command. By default the user's password can be retained through a grace period (15 minutes per pseudo terminal), allowing the user to execute several successive commands as the requested user without having to provide a password again.


more here [https://en.wikipedia.org/wiki/Sudo](https://en.wikipedia.org/wiki/Sudo)

---

