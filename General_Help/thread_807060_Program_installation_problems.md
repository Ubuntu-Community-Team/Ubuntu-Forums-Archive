---
title: "Program installation problems"
date: 2008-05-25
forum: General Help
---

### Post by Swarley on 2008-05-25
Whenever i try to install anything through a terminal or through synaptic it tells me:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Can someone tell me what this means and how to fix it?

---

### Post by shifty_powers on 2008-05-25
have you tried the command in a terminal?

and irc, it just means that the system was stopped from finishing an installation.

just

```
dkg --configure -a
```

in a terminal, applications>accessories>terminal, and it should fix it ;)

---

### Post by lud666 on 2008-05-25
Have you tried running "dpkg --configure -a" in terminal like it says?

---

### Post by Swarley on 2008-05-25
Whenever i try running "dpkg --configure -a" it tells me:

"dpkg: requested operation requires superuser privilege"

---

### Post by koenn on 2008-05-25
```
**sudo** dpkg --configure -a
```

---

### Post by shifty_powers on 2008-05-25
heh whoops, yeah sorry forgot that ;)

---

### Post by woztron on 2008-05-26
Ok, i have the same problem and though i'm still quite n00bish i got that far on my own.

The problem when i try the 

sudo dpkg --configure -a

it starts running then the same error crops up and stops/freezes the terminal.

The problem is on a remote machine running hardy server and uninstalling mysql-server (can't get it work properly for torrentflux but thats another issue).  This is what i get in my terminal when the process stops:


woz@wozserver:~$ sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                 [ OK ]
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.


The second * is yellow by the way.

Any idea what i can do solve this problem?

---

