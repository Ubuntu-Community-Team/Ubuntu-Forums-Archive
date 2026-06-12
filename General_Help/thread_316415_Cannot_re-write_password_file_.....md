---
title: "Cannot re-write password file ...."
date: 2006-12-10
forum: General Help
---

### Post by Pootle on 2006-12-10
Breezy, AMD64

I'm having problems installing packages as adduser is failing to re-write the  password file. 

The GUI User/Group utility does not have problems .. but from a command line (with sudo) the shadow utility pwunconv also fails to rewrite the password file.  

pwck works and reports no problems apart from missing directories. 

The only google reference to this problem seemed to be a SELinux bug or errors caused by manually editing /etc/passwd.  

Done the obvious things like check permissions, removed lock files etc, lots of disk space, user and group not already existing (both passwd, group and respective shadow files).  

Anyone any ideas on what's causing the issue?  PAM?

It seemed to manifest when I was loading SSH related stuff for rdiff-backup a few weeks ago to facilitate backing up to a redundant server. At that time it was openssh-server that failed because of the same inability to re-write the password file.

I usually manage to sort most things myself but this one has me scratching my head, so any help gratefully appreciated.

---

### Post by taurus on 2006-12-10
How did you add a new user from a command line again?

---

### Post by Pootle on 2006-12-10
It fails from adduser on the command line, but the GUI manage user/group works .....

---

### Post by taurus on 2006-12-10
How did you run it from a command line?

---

### Post by Pootle on 2006-12-10
robert@studioserver:~$ sudo adduser bloggs
Adding user `bloggs'...
Adding new group `bloggs' (1003).
Adding new user `bloggs' (1003) with group `bloggs'.
adduser: `/usr/sbin/useradd -d /home/bloggs -g bloggs -s /bin/bash -u 1003 bloggs' returned error code 1.  Aborting.
Cleaning up.
Removing user `bloggs'.
Removing group `bloggs'.

---

### Post by taurus on 2006-12-10
Post the output of these two commands here!

```
cat /etc/group
cat /etc/passwd
```

---

### Post by Pootle on 2006-12-10
> **taurus said:**
> Post the output of these two commands here!

```
cat /etc/group
cat /etc/passwd
```
Hope this works

> /etc/group
root:*:0:
daemon:*:1:
bin:*:2:
sys:*:3:
adm:*:4:robert
tty:*:5:
disk:*:6:
lp:*:7:cupsys
mail:*:8:
news:*:9:
uucp:*:10:
man:*:12:
proxy:*:13:
kmem:*:15:
dialout:*:20:robert,cupsys
fax:*:21:
voice:*:22:
cdrom:*:24:robert,hal
floppy:*:25:robert,hal
tape:*:26:
sudo:*:27:
audio:*:29:robert
dip:*:30:robert
www-data:*:33:
backup:*:34:
operator:*:37:
list:*:38:
irc:*:39:
src:*:40:
gnats:*:41:
shadow:*:42:
utmp:*:43:
video:*:44:robert
sasl:*:45:
plugdev:*:46:robert,hal
staff:*:50:
games:*:60:
users:*:100:
nogroup:*:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
robert:!:1000:
lpadmin:!:104:robert
scanner:!:105:robert
admin:!:106:robert
crontab:!:107:
ssh:!:108:
hal:!:110:
slocate:!:111:
saned:!:112:
gdm:!:113:
postdrop::500:
dhcpd:!:114:
ftpuser:!:1001:
abbeyhou:!:1002:
mysql:!:115:


/etc/passwd
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
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
robert:x:1000:1000:robertlawrence,,,:/home/robert:/bin/bash
cupsys:x:100:104::/home/cupsys:/bin/false
messagebus:x:104:100::/var/run/dbus:/bin/false
fetchmail:x:105:65534::/var/run/fetchmail:/bin/sh
hal:x:110:110:Hardware abstraction layer,,,:/var/run/hal:/bin/false
saned:x:112:112::/home/saned:/bin/false
gdm:x:106:113:Gnome Display Manager:/var/lib/gdm:/bin/false
hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false
postfix:x:500:500:postfix:/etc/postfix:/bin/sh
dhcpd:x:114:114::/nonexistent:/bin/false
ftp:x:108:65534::/home/ftp:/bin/false
ftpuser:x:1001:1001::/home/FTP-shared:/bin/false

---

### Post by taurus on 2006-12-10
```
sudo useradd -m -s /bin/bash bloggs
sudo passwd bloggs
```

---

### Post by Pootle on 2006-12-10
useradd: cannot rewrite password file

---

### Post by Pootle on 2006-12-10
useradd: cannote rewrite password file

---

### Post by taurus on 2006-12-10
Did you happen to open "GUI manage User/Group" while you ran that command from a terminal?  Otherwise, paste the output of this command here.

```
ls -la /etc/group /etc/passwd
```

---

### Post by Pootle on 2006-12-10
Nope the GUI wasn't open .....

ls -al /etc/passwd /etc/group

-rw-r--r--  1 root root  796 2006-12-11 00:02 /etc/group
-rw-r--r--  1 root root 1440 2006-12-10 18:57 /etc/passwd

---

### Post by Pootle on 2006-12-10
And in case it's of interest here is the output from /var/log/auth.log

Dec 11 00:23:41 localhost sudo:   robert : TTY=pts/1 ; PWD=/home/robert ; USER=root ; COMMAND=/usr/sbin/useradd -m -s /bin/bash bloggs
Dec 11 00:23:42 localhost useradd[14965]: new user: name=bloggs, uid=1002, gid=100, home=/home/bloggs, shell=/bin/bash
Dec 11 00:23:42 localhost useradd[14965]: failed adding user `bloggs', data deleted

---

### Post by taurus on 2006-12-10
What happens if you try to add a user with another name like john?  Do you still get the same error message?

---

### Post by Pootle on 2006-12-11
Any username causes the same issue.  This HAS to be a security problem stopping the passwd file being re-written doesn't it?

I'm currently doing an strace on this machine and another to see if I can spot where the difference is ... it's currently writing an error to stderr about sudo must be setuid (which it is!)

Appreciate the help so far .....

---

