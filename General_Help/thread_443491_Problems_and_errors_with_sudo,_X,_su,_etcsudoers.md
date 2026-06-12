---
title: "Problems and errors with sudo, X, su, /etc/sudoers"
date: 2007-05-14
forum: General Help
---

### Post by MMMMManuel on 2007-05-14
Hi!
I'm using ubuntu + kde (installed after some week) kernel 2.6 on AMD64.

Some days ago I have reinstalled eclipse with synaptic and I turned off. When I turned on again:
- I can't use synaptic or adept because this is the message```

Su returned with an error.
```
```
$ sudo synaptic
sudo: can't open /etc/sudoers: Permission denied
```
-  I can start synaptic without privileges, because if i wrote```
$ synaptic
```
synaptic starts, but I can't install anything, obviously
- If I log as root this happens:```
# synaptic
(synaptic:8923): Gtk-WARNING **: cannot open display:
```
or this```
# adept 
adept: ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.
```

Permissions of sudo:```
# ls -al /usr/bin/sudo 
-rwsr-xr-x 1 root root 110280 2006-05-17 10:43 /usr/bin/sudo
```

This is my /etc/sudoers```

# ls -l /etc/sudoers
-r--r----- 1 root root 422 2007-05-12 12:00 /etc/sudoers

Defaults        !lecture,tty_tickets,!fqdn

root    ALL=(ALL) ALL

%admin ALL=(ALL) ALL
```
The syntax is correct:```
# visudo -c
/etc/sudoers file parsed OK
```

I tried to change %admin with my username and to add```
 myusername  ALL=(ALL) ALL
``` but nothing changes.

I reinstall sudo, synaptic, adept... but nothing to do.
I can't change permissions of sudoers file because if I try to use "sudo" with permissions different from 0440 I have this message```
$ sudo adept
sudo: /etc/sudoers is mode 0755, should be 0440
```

If usefull, I post this:```
# stat /etc/sudoers
  File: `/etc/sudoers'
  Size: 428             Blocks: 8          IO Block: 4096   regular file
Device: 1601h/5633d     Inode: 1929718     Links: 1
Access: (0440/-r--r-----)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2007-05-14 20:07:32.000000000 +0200
Modify: 2007-05-14 20:07:32.000000000 +0200
Change: 2007-05-14 20:07:53.000000000 +0200
```
```
# stat /usr/bin/sudo
  File: `/usr/bin/sudo'
  Size: 110280          Blocks: 224        IO Block: 4096   regular file
Device: 1601h/5633d     Inode: 1962471     Links: 1
Access: (4755/-rwsr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2007-05-14 20:07:55.000000000 +0200
Modify: 2006-05-17 10:43:41.000000000 +0200
Change: 2007-05-12 23:22:59.000000000 +0200
```

And also this, which is another problem (linked, I think):```
# kate /etc/sudoers
kate: cannot connect to X server
```

What should I do?

---

### Post by taurus on 2007-05-14
First, you should belong to groups adm and admin in /etc/group if you want to use sudo.  Modifying /etc/sudoers is not a great idea if you don't know what you are doing.  

So, boot into recovery mode from GRUB menu and run

```
chmod 440 /etc/sudoers
```
Then, reboot and log back in with your username and password.  Now, post the output of this command here?

```
id
```

---

### Post by MMMMManuel on 2007-05-14
>  	First, you should belong to groups adm and admin in /etc/group if you want to use sudo.
Yes, but friday I was able to use it... only after the update I'm not able to do it...

I can't use chmod on /etc/sudoers into recovery mode.
```
$ id
uid=1000(mastrofini) gid=1000(mastrofini) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(mastrofini)

```


Anyway, before modifying the file, I read what to do.

---

### Post by MMMMManuel on 2007-05-15
Nobody can help me? :confused:

---

### Post by MMMMManuel on 2007-05-16
Solution:```

chmod 775 / 
```
Bad.

---

