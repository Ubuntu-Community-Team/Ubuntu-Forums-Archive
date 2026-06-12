---
title: "[SOLVED] Can't get system services to start in Ubuntu"
date: 2008-02-24
forum: General Help
---

### Post by crispinb on 2008-02-24
According to what I understand of the init scripts, I have both samba and sshd configured to start automatically.

For example: 
```

sudo update-rc.d -n samba defaults
 System startup links for /etc/init.d/samba already exist
```

There are appropriate 'Sxxx' links to /etc/init.d/samba and /etc/init.d/ssh in /etc/rc2.d. They also appear ticked in System->Administration->Services

But for some reason these services don't start automatically. They both run fine if I manually to an /etc/init.d/xxx start.

Any ideas re what the problem might be?

---

### Post by Zeroangel on 2008-02-25
From what I know of shell scripts first ya gotta:

1) Create your script in /etc/init.d, ensure the first line of the script is
```
#! /bin/sh
```
2) Set the script as executable. It doesnt need to have a .sh extension.

3) Create a symbolic link to the script in the rcS.d folder.
```
sudo ln -s /etc/init.d/myscript /etc/rcS.d/S90myscript
```Where the number after S is the order you want the script to start in.

---

### Post by crispinb on 2008-02-25
Thanks zeroangel, but that's not quite my problem. the scripts and links exist fine, as installed by the respective packages. I can run, for example, *sudo /etc/init.d/ssh start * or *sudo /etc/rc2.d/ssh start*, and sshd starts up and functions perfectly. 

But for some reason neither sshd nor samba will start up automatically on boot. I've checked the symbolic links manually and with update-rc.d. 

I'm puzzled.

---

### Post by crispinb on 2008-03-02
Anyone have any idea on this? I've racked my brain reading what docs I can find. As far as I understand, these services should be starting, but they're not. 

(incidentally, the weird services admin app supplied with gnome doesn't help. It's downright confusing, as it only seems to show a subset of services)

---

### Post by crispinb on 2008-03-13
OK, fixed. I must have missed some problem with the symlinks. To fix, I used update-rc.d again , but ran 'sudo update-rc.d -f <servicename> remove' first, as apparently updte-rc.d won't touch links that are already there.

---

