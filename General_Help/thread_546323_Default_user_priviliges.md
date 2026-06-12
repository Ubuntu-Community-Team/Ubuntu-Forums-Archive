---
title: "Default user priviliges"
date: 2007-09-08
forum: General Help
---

### Post by Linuxman33 on 2007-09-08
Could someone tell me the default user privileges (like of the first account thats made when your setting up ubuntu, not the root)

I was messing around changing the root's password and i accidently changed my username to root.

I got that mess sorted out and the onlything i need to know are the default user privileges

---

### Post by merlinus on 2007-09-08
owner = read+write (create and delete files)
group = read only (access files)
others= read only (access files)

-merlin

---

### Post by chalex on 2007-09-08
```
alex@user-desktop:~$ id 
uid=1000(alex) gid=1000(alex) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(alex)

```

That is, my /etc/group looks like this:
```

alex@user-desktop:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:alex
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,alex
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,alex
floppy:x:25:haldaemon,alex
tape:x:26:
sudo:x:27:
audio:x:29:alex
dip:x:30:alex
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:alex
sasl:x:45:
plugdev:x:46:haldaemon,alex
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,alex
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:alex
lpadmin:x:113:alex
haldaemon:x:114:
powerdev:x:115:haldaemon,alex
slocate:x:116:
admin:x:117:alex
gdm:x:118:
fuse:x:119:
alex:x:1000:
ntp:x:120:

```

I'm not familiar enough with the GUI to tell you how to add yourself to all those groups, but you can use a text editor on /etc/group and add your username there.  You'll need to log out and log back in afterwards.

Obviously, my username is "alex", Ubuntu Feisty.

---

### Post by merlinus on 2007-09-08
System/Administration./Users and Groups

-merlin

---

### Post by Linuxman33 on 2007-09-08
Thanks everybody, got it fixed

---

