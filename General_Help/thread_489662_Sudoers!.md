---
title: "Sudoers!"
date: 2007-07-01
forum: General Help
---

### Post by nephron222 on 2007-07-01
Can someone tell me how to add sudoers?

I did the command EDITOR=gedit sudo visudo and put:

user ALL=(ALL) ALL under the root and

user ALL=(ALL) ALL under the %admin but i still have all the permissions. What do i do?

---

### Post by CocoAUS on 2007-07-01
I'm not sure what "guide" you were using to add users to the sudoers file, nor am I sure what you meant by "i still have all the permissions."

To add sudoers, simply add a line under 'root ALL=(ALL) ALL' that says the same thing, replacing root with whatever username you want to add to sudo.  Save it, then whatever user you added should be able to use sudo.

---

### Post by nephron222 on 2007-07-01
Ok so i made a test and tried to delete something from /usr/share/pixmap and tryed to delete an icon from there that i inserted with nautilus. It still said i had no permission to delete that file. 

This is my "sudo visudo"

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
offir ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
offir ALL=(ALL) ALL

```

---

### Post by kerry_s on 2007-07-01
I think your miss understanding the purpose of the sudoers file, it simply allows you to use gksu,gksudo,sudo and sudo su.

example:
use> gksu nautilus
enter your password
then go to /usr/share/pixmap and you can delete anything you want.

just because your in the sudoers file, doesn't mean you bypass security.

there are several forms of sudo.

gksu <launches a graphical application as root and always asks for password
gksudo <launches a graphical application as root, but can bypass the password if told to in sudoers.
sudo <run commands in terminal as root
sudo su <changes you to root in terminal


now if you trying to add another user that you want to have root permission's, you would just simply add the name to the group "admin" using the users & groups application or manually(gksu gedit /etc/group).

```
admin:x:4:(the person who installed),(your user you want to add)
```

---

### Post by nephron222 on 2007-07-02
ya i did that. I marked the check box next to my name in the admin group but i still cant do anything and have to use nautilus...

---

### Post by kerry_s on 2007-07-02
gedit /etc/group

select all, then copy and paste here so we can see.

and it's suppose to be the other way around, you need to add yourself to the "admin" group, not the admin group to you. the name is "admin" not your name, add your name there. do it manually if you cant figure it out in the application.

---

### Post by nephron222 on 2007-07-02
gedit /etc/group 

```

root:x:0:offir
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:offir
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,offir,mythtv
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,offir,mythtv
floppy:x:25:haldaemon,offir
tape:x:26:
sudo:x:27:offir
audio:x:29:mythtv,offir
dip:x:30:offir
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:mythtv,offir
sasl:x:45:
plugdev:x:46:haldaemon,offir
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
lpadmin:x:109:offir
haldaemon:x:110:
scanner:x:111:cupsys,hplip,offir
slocate:x:112:
gdm:x:113:
fuse:x:114:
ntfs:x:1000:
mysql:x:115:
Debian-exim:x:116:
mythtv:x:117:
clamav:x:118:
snort:x:119:
offir:x:1001:
admin:x:120:offir
avahi-autoipd:x:121:
netdev:x:122:
nvram:x:123:
powerdev:x:124:haldaemon
ntp:x:125:
dirmngr:x:126:
vboxusers:x:1002:offir

```

---

