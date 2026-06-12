---
title: "messed up my fresh edgy install!"
date: 2006-11-21
forum: General Help
---

### Post by tempo500 on 2006-11-21
fresh edgy install and modified /etc/group, fstab and /etc/hosts for nfs and drqueue. everything looks ok but i cant start some programs from system/administration...like user and groups, shared folders, services and networking. i guess there is a problem in my /etc/group file? some help on this? please?

when i start users-admin i get(no difference with sudo):
```
users-admin

(users-admin:6237): Liboobs-CRITICAL **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends was not provided by any .service files

(users-admin:6237): Liboobs-CRITICAL **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends was not provided by any .service files
```

/etc/group file
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:phil,tmp
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,phil,tmp
fax:x:21:tmp
voice:x:22:
cdrom:x:24:haldaemon,phil,tmp
floppy:x:25:haldaemon,phil,tmp
tape:x:26:tmp
sudo:x:27:
audio:x:29:phil,tmp
dip:x:30:phil,tmp
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:phil
sasl:x:45:
plugdev:x:46:haldaemon,phil,tmp
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:phil
haldaemon:x:110:
scanner:x:111:cupsys,hplip,phil,tmp
slocate:x:112:
gdm:x:113:
phil:x:1000:
admin:x:114:phil,tmp
tmp:x:1001:
ntp:x:115:
```

my /etc/hosts file:
```
127.0.0.1 	localhost
127.0.1.1 	workstation

192.168.2.103	workstation	workstation.workgroup.local
192.168.2.102	render 		render.workgroup.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by phil.rhinehart on 2007-02-11
I am having the same problem. I have posted a similar post here -> [http://ubuntuforums.org/showthread.php?t=356634](http://ubuntuforums.org/showthread.php?t=356634)
Nobody has responded yet and I have been unable to find a solution anywhere else on the web.

Have you figured anything out yet?

---

