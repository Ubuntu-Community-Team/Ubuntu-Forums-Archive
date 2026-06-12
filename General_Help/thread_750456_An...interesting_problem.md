---
title: "An...interesting problem"
date: 2008-04-09
forum: General Help
---

### Post by caesarcardinale on 2008-04-09
Hey guys,
  I've been using linux for a little while now, but Gutsy has just done something weird.  The system has stopped asking for the administrative password.  Any time I try to open an administrative tool (like Networking, or installing a program) it doesn't ask for the password and then either doesn't start the administrative tool or the installation of a program stops and gives me an error.  I can still install using the terminal, but that's not the issue.  No tool that needs an administrative password works because it won't give me the prompt to enter it.  Any ideas?

PS: This problem just started, one day it was working fine, the next this happens and I'm don't remember making any alterations to the system in the meantime.

---

### Post by Seti on 2008-04-09
Do you recall doing anything that may have changed your users rights on the machine at all?
On a hunch, tell us what you see under /etc/group  and post it here.

---

### Post by caesarcardinale on 2008-04-09
This is the entry of /etc/group--my username is antonino

[PHP]proxy:x:13:
kmem:x:15:
dialout:x:20:antonino
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,antonino
floppy:x:25:haldaemon,antonino
tape:x:26:
sudo:x:27:
audio:x:29:antonino
dip:x:30:antonino
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:antonino
sasl:x:45:
plugdev:x:46:haldaemon,antonino
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,antonino
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:antonino
messagebus:x:109:
admin:x:110:antonino
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:antonino
haldaemon:x:116:
powerdev:x:117:haldaemon,antonino
gdm:x:118:
slocate:x:119:
antonino:x:1000:[/PHP]

---

### Post by sisco311 on 2008-04-09
Pleas post the output of the **id** command.

---

### Post by caesarcardinale on 2008-04-09
Here you go, the output of the id command

uid=1000(antonino) gid=1000(antonino) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),
46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),
1000(antonino)

---

### Post by sisco311 on 2008-04-09
what happens when you run a program with gksudo:
```
gksudo update-manager
```

---

### Post by sisco311 on 2008-04-09
sorry double post

---

### Post by caesarcardinale on 2008-04-09
gksudo update-manager didn't really do anything.  It didn't give me an error and the program didn't open, it just moved me to the next line in the terminal.

when I ran update-manager as root, it opened but also gave me this error

warning: could not initiate dbus

---

