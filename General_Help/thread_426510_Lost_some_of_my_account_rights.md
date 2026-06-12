---
title: "Lost some of my account rights"
date: 2007-04-28
forum: General Help
---

### Post by OOzypal on 2007-04-28
I was trying to add my login name to group www-data so I did

usermod -g www-data hab
usermod -G www-data hab

now, I lost my system menu. When I click on System I see only limited
items. How can I re-gain my rights.

my /etc/group

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
www-data:x:33:hab
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
messagebus:x:104:
ssl-cert:x:105:cupsys
crontab:x:106:
ssh:x:107:
avahi-autoipd:x:108:
avahi:x:109:
netdev:x:110:
lpadmin:x:111:
haldaemon:x:112:
powerdev:x:113:haldaemon
scanner:x:114:cupsys,hplip
slocate:x:115:
admin:x:116:
gdm:x:117:
fuse:x:118:
hab:x:1000:
nvram:x:119:
mysql:x:120:
ntp:x:121:
```

---

### Post by trak87 on 2007-04-28
I've never used the usermod command using the graphical User/Groups manager instead, but the man page for usermod shows this for the -G option you used:

> -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
A list of supplementary groups which the user is also a member of. Each group 
is separated from the next by a comma, with no intervening whitespace. The groups 
are subject to the same restrictions as the group given with the -g option. [B]If the user 
is currently a member of a group which is not listed, the user will be removed from the 
group. This behaviour can be changed via -a option, which appends user to the 
current supplementary group list.[/B]

So I think you removed yourself from all the groups you previously belonged to by not using the -a option.

When I do a grep on all the groups I belong to (in Feisty), I get this list. Perhaps you can use this list to rejoin those lost groups:

adm
dialout
cdrom
floppy
audio
dip
video
plugdev
scanne
netdev
lpadmin
powerdev
admin

---

### Post by aysiu on 2007-04-28
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

