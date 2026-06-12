---
title: "[SOLVED] Gnome permissions after restoring passwd,group,shadow."
date: 2008-05-10
forum: General Help
---

### Post by CheShA on 2008-05-10
OK so I jusr reinstalled hardy, a clean install to replace my previous install which was upgraded from gutsy. FWIW I did the install via debootstrap +  chroot + apt-get ubuntustudio-desktop, etc.  not from CD. Anyway, I have just copied over my old /etc/group /etc/passwd /etc/shadow /etc/gshadow from backup and, while most things seem fine, I am getting a few permissions issues when trying to do admin-type things in Gnome.

For example, when I go to System > Administration > Network I get "Configuration could not be loaded. You are not allowed to access the system configuration".

If I try to mount external USB HDD I get "Cannot mount volume.  Error org.freedesktop.DBus.Error.AccessDenied"

I assume this is related to policykit and there are more config files I need to copy over to get the policykit permissions in line with the UIDs that exist now. Does anyone know what I'm missing?

---

### Post by CheShA on 2008-05-10
Posting /etc/passwd since it may be related. Notice things like policykit user are added on as an afterthought because this passwd was restored from an upgraded hardy, not a clean install.

```

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
ntp:x:103:109::/home/ntp:/bin/false
cheshacat:x:1000:1000:CheShA Cat,,,,:/home/cheshacat:/bin/bash
messagebus:x:104:112::/var/run/dbus:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:106:114:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:115:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:108:117:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:109:119:Gnome Display Manager:/var/lib/gdm:/bin/false
lowri:x:1001:1001:Lowrilingus,,,,:/home/lowri:/bin/bash
public:x:1003:1003:Hoi Polloi,,,,:/home/public:/bin/bash
smbguest:x:1004:1005:Samba guest account:/dev/null:/bin/false
xbox:x:1005:1005:Xbox,,,,:/dev/null:/bin/false
lowribackup:x:1006:1009:Lowri Backup Account,,,,:/dev/null:/bin/false
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
website-sync:x:1007:1010:Website sync,,,,:/home/cheshacat/Backup type stuff/Website backups:/bin/bash
eeepc-backup:x:1008:1011:eeepc-backup,,,,:/home/eeepc-backup:/bin/false
libuuid:x:111:122::/var/lib/libuuid:/bin/sh
pulse:x:112:125:PulseAudio daemon,,,:/var/run/pulse:/bin/false
polkituser:x:113:128:PolicyKit,,,:/var/run/PolicyKit:/bin/false

```

---

### Post by CheShA on 2008-05-10
posting /etc/group since it may be related. Do I need to add myself to the polkituser group? Also I just realised that th pre3vious install had linux-image-rt, new install is generic kernel.


```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:cheshacat
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cheshacat
fax:x:21:cheshacat
voice:x:22:
cdrom:x:24:haldaemon,lowri,public,cheshacat
floppy:x:25:haldaemon,lowri,cheshacat
tape:x:26:cheshacat
sudo:x:27:
audio:x:29:lowri,public,cheshacat,pulse
dip:x:30:cheshacat
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
plugdev:x:46:haldaemon,lowri,public,cheshacat
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,lowri,cheshacat
nvram:x:105:
fuse:x:106:cheshacat
crontab:x:107:
ssh:x:108:
ntp:x:109:
cheshacat:x:1000:
ssl-cert:x:110:
lpadmin:x:111:
messagebus:x:112:
admin:x:113:cheshacat
avahi-autoipd:x:114:
avahi:x:115:
netdev:x:116:
haldaemon:x:117:
powerdev:x:118:haldaemon
gdm:x:119:
slocate:x:120:
lowri:x:1001:
public:x:1003:cheshacat,public,lowri
mp3zwritable:x:1004:cheshacat,lowri,lowribackup
nobody:x:1005:
sambamachines:x:1006:
winbindd_priv:x:121:
xbox:x:1007:
downloads:x:1008:cheshacat,lowri
lowribackups:x:1009:lowri,lowribackup
website-sync:x:1010:cheshacat,website-sync
eeepc-backup:x:1011:
libuuid:x:122:
mlocate:x:123:
sambashare:x:124:cheshacat
pulse:x:125:
pulse-access:x:126:
pulse-rt:x:127:
polkituser:x:128:

```

---

### Post by CheShA on 2008-05-11
bump?

---

### Post by CheShA on 2008-05-11
Sack it, I redid the process excluding the  system generated accounts by following [URL="
http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/"]this howto[/URL]

NB that for ubuntu UGIDLIMIT=1000

---

