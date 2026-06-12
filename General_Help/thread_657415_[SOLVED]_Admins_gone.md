---
title: "[SOLVED] Admins gone"
date: 2008-01-03
forum: General Help
---

### Post by cgeorge1122 on 2008-01-03
[CENTER]PLEASE NOTE THAT I AM A COMPLETE LINUX NOOB[/CENTER]

Yesterday I installed Ubuntu for the first time on my computer (before I was running XP Media Center), so that it would dual boot. Today, before I had my coffee, I did something with user accounts and now it appears that nobody is an administrator. I phoned my friend up and he said to try some terminal command.

This is what he said to do, type ```
groups matt
```

This is what it yielded:
```
matt@patronuss:~$ groups matt
matt : matt adm dialout cdrom floppy audio dip video plugdev scanner netdev powerdev
```

He also said to type ```
su
```

This is what happened:
```
matt@patronuss:~$ su
Password:
su: Authentication failure
Sorry.
```
For [SIZE="1"]Password:[/SIZE] I typed in the correct password.

If anyone knows what is going on, could you please help me,,,

thanks

---

### Post by PeterJS on 2008-01-03
Ubuntu uses sudo and no su, just an FYI for future refence. Now to get your admin account back up boot into recovery mode, open a terminal and run:
```

usermod -a -G admin username

```
The -a is for append, and the -G tells it the thing you're adding is a seconday group, and then the username tells it which user you're doing this stuff to.

---

### Post by immortal_cro on 2008-01-03
Try nothing as password for su, just press enter.
Or try booting recovery mode, select recovery mode from grub menu and then add yourself to the admin group.

---

### Post by solar george on 2008-01-03
> Ubuntu uses sudo and no su
Also,
If you use sudo you will only need your own password to access the admin (called root) account - if you use su you will need the admin password which is disabled on ubuntu by default.

Edit: To get an admin (root or superuser) terminal use the command sudo -s

---

### Post by cgeorge1122 on 2008-01-03
@ PeterJS:
I've booted into recovery mode, but whenever I enter ```
usermod -a -G admin matt
``` into terminal it gives me this:

```
matt@patronuss:~$ usermod -a -G admin matt
usermod: unable to lock password file
```

hoping for help,
matt

---

### Post by solar george on 2008-01-04
You do not need to be a member of an admin group as long as you can run sudo - on my laptop there is not even any admin group.

---

### Post by RC Howe on 2008-01-04
It may help you to edit the sudoers file and add yourself. Use visudo so you don't break things.```
# visudo
``` Add yourself or %admin.

---

### Post by cgeorge1122 on 2008-01-16
Since I don't have much on it I've decided to reformat that section of my hard drive, it works now thanks for all your help!!

---

