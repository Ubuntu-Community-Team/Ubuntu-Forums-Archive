---
title: "Newb move using usermod -G"
date: 2007-01-21
forum: General Help
---

### Post by krisstech on 2007-01-21
I was attempting to follow the proftpd guide here: [http://archiv.debianhowto.de/en/proftpd/c_proftpd.html](http://archiv.debianhowto.de/en/proftpd/c_proftpd.html) and I executed the following command as root.

addgroup *ftpuser*
usermod -G ftpuser *username*

for the username portion i added the username of my account. Afterwards, i wasn't able to sudo anything. I wish to remove the group ftpuser and restore my account to its original group settings. 

Note: I also backed up my /etc/groups file and removed the line:

```
ftpuser:x:1001:kriss
```

please advise

---

### Post by krisstech on 2007-01-21
Here is my current /etc/groups file:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon
floppy:x:25:haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
crontab:x:104:
ssh:x:105:
lpadmin:x:106:
messagebus:x:107:
haldaemon:x:108:
slocate:x:109:
scanner:x:110:cupsys
gdm:x:111:
kriss:x:1000:
admin:x:112:
ftpuser:x:1001:

```

---

### Post by krisstech on 2007-01-21
Can someone at least post their /etc/group   file?

---

