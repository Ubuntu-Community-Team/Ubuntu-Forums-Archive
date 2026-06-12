---
title: "groups: cannot find name for group ID xxxxxxx"
date: 2014-01-07
forum: General Help
---

### Post by vasilios2 on 2014-01-07
After a reboot today this started popping up whenever I open a new terminal window:

groups: cannot find name for group ID 495452673
groups: cannot find name for group ID 495453268
groups: cannot find name for group ID 495453350
groups: cannot find name for group ID 495453401

vbetoglou@helios:/var/log$ groups && echo $GROUPS
vbetoglou adm cdrom sudo dip plugdev lpadmin sambashare groups: cannot find name for group ID 495452673
495452673 groups: cannot find name for group ID 495453268
495453268 groups: cannot find name for group ID 495453350
495453350 groups: cannot find name for group ID 495453401
495453401
vbetoglou@helios:/var/log$ id
uid=1000(vbetoglou) gid=1000(vbetoglou) groups=1000(vbetoglou),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare),495452673,495453268,495453350,495453401

Can someone point me in the right place to start looking as to what is causing this?

Regards,
Bill

---

### Post by bab1 on 2014-01-07
> **vasilios2 said:**
> After a reboot today this started popping up whenever I open a new terminal window:

groups: cannot find name for group ID 495452673
groups: cannot find name for group ID 495453268
groups: cannot find name for group ID 495453350
groups: cannot find name for group ID 495453401

vbetoglou@helios:/var/log$ groups && echo $GROUPS
vbetoglou adm cdrom sudo dip plugdev lpadmin sambashare groups: cannot find name for group ID 495452673
495452673 groups: cannot find name for group ID 495453268
495453268 groups: cannot find name for group ID 495453350
495453350 groups: cannot find name for group ID 495453401
495453401
vbetoglou@helios:/var/log$ id
uid=1000(vbetoglou) gid=1000(vbetoglou) groups=1000(vbetoglou),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare),495452673,495453268,495453350,495453401

Can someone point me in the right place to start looking as to what is causing this?

Regards,
Bill
I'm not sure what the answer will be in the end, but you can see all the groups in the /etc/group file using this ```
getent group
```

These look like SID ID numbers that Samba has preserved.  Do you have files or directories that have this group ID?

If it was my machine I would make a copy of the /etc/group file and then edit the original.  First I  would delete the groups from your ID and then remove the offending groups from the file.  You can use ***deluser*** to do the deletion.

On the files and directories you can use ```
sudo chgrp <group> file   # or dir
```

---

### Post by vasilios2 on 2014-01-17
vbetoglou@helios:~$ getent group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:vbetoglou
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:vbetoglou
floppy:x:25:
tape:x:26:
sudo:x:27:vbetoglou
audio:x:29:pulse
dip:x:30:vbetoglou
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
plugdev:x:46:vbetoglou
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
avahi-autoipd:x:106:
ssl-cert:x:107:
lpadmin:x:108:vbetoglou
netdev:x:109:
whoopsie:x:110:
mlocate:x:111:
ssh:x:112:
utempter:x:113:
rtkit:x:114:
bluetooth:x:115:
lightdm:x:116:
nopasswdlogin:x:117:
avahi:x:118:
scanner:x:119:
colord:x:120:
pulse:x:121:
pulse-access:x:122:
saned:x:123:
vbetoglou:x:1000:
sambashare:x:124:vbetoglou
gdm:x:125:
mdm:x:126:
mysql:x:127:
elasticsearch:x:128:
clamav:x:129:
svn:x:1001:vbetoglou

I don't see those IDs listed?

---

### Post by vasilios2 on 2014-01-17
groups: cannot find name for group ID 495452673
groups: cannot find name for group ID 495453268
groups: cannot find name for group ID 495453350
groups: cannot find name for group ID 495453401
vbetoglou@helios:~$ sudo deluser vbetoglou 495452673
[sudo] password for vbetoglou: 
/usr/sbin/deluser: The group `495452673' does not exist.

---

### Post by bab1 on 2014-01-17
> **vasilios2 said:**
> groups: cannot find name for group ID 495452673
groups: cannot find name for group ID 495453268
groups: cannot find name for group ID 495453350
groups: cannot find name for group ID 495453401
vbetoglou@helios:~$ sudo deluser vbetoglou 495452673
[sudo] password for vbetoglou: 
/usr/sbin/deluser: The group `495452673' does not exist.

Did you just delete your user group?  Post the output of ```
getent group vbetoglou 
```

---

### Post by jeanjd63 on 2014-01-17
Hello
You can try  :
**sudo addgroup -gid **[COLOR=#000000]***495452673[I] g1***
[/I][/COLOR]and so one for others numbers
and after 
[B]sudo  delgroup [COLOR=#000000][I]g1
[/I][/COLOR][/B][COLOR=#000000]and so one [/COLOR]**[COLOR=#000000][/COLOR]**

---

