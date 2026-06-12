---
title: "[SOLVED] superuser doesn't have permission to run bash"
date: 2008-03-06
forum: General Help
---

### Post by caughran on 2008-03-06
Something is fouled with bash. There is apparently no permission great enough to run a script. The problem happens with other scripts, not just this one.

```
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ sudo ./flashplayer-installer
[sudo] password for jim:
sudo: unable to execute ./flashplayer-installer: Permission denied
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ ls -l
total 7968
-rwxrwxrwx 1 jim jim   21700 2007-11-20 18:24 flashplayer-installer
-rwxr-xr-x 1 jim jim 8119784 2007-11-20 18:24 libflashplayer.so

```
I discovered that /bin/sh pointed to dash, not to bash, so I changed that and rebooted, to no effect. I also tried reinstalling bash with synaptic.

```
im@JIMJANET:~/Desktop$ cd /bin
jim@JIMJANET:/bin$ ls -l sh*
lrwxrwxrwx 1 root root 4 2008-03-03 15:51 sh -> bash
lrwxrwxrwx 1 root root 4 2007-05-27 16:15 sh.dash -> dash

```
and even
```
jim@JIMJANET:~/tempstuf/install_flash_player_9_linux$ sudo -i
[sudo] password for jim:
root@JIMJANET:~# /home/jim/tempstuf/install_flash_player_9_linux/flashplayer-installer
-bash: /home/jim/tempstuf/install_flash_player_9_linux/flashplayer-installer: /bin/sh: bad interpreter: Permission denied

```

---

### Post by Bliepo32 on 2008-03-06
Does your account has the permission to do administrative task? Are you sure you entered the correct password?

---

### Post by caughran on 2008-03-07
> **Bliepo32 said:**
> Does your account have the permission to do administrative task? Are you sure you entered the correct password?

Yes and yes; there have been no problems.

With general permission to run a script, the same error happens when run from terminal.

---

### Post by Front187 on 2008-03-07
What are the contents of /etc/group?

---

### Post by Oldsoldier2003 on 2008-03-07
> **Front187 said:**
> What are the contents of /etc/group?
or run
```
id
``` in a terminal to see what groups the account is assigned to.

---

### Post by Front187 on 2008-03-07
> **Oldsoldier2003 said:**
> or run
```
id
``` in a terminal to see what groups the account is assigned to.

You learn something new every day. :-D

---

### Post by caughran on 2008-03-07
> **Front187 said:**
> What are the contents of /etc/group?

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:jim,janet,scheduled,kde
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,jim,janet,root,scheduled,kde
fax:x:21:janet,scheduled,kde
voice:x:22:
cdrom:x:24:haldaemon,jim,janet,root,scheduled,kde
floppy:x:25:haldaemon,jim,janet,root,scheduled,kde
tape:x:26:janet,root,scheduled,kde
sudo:x:27:
audio:x:29:jim,janet,root,scheduled,kde
dip:x:30:jim,janet,scheduled,kde
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:jim
sasl:x:45:
plugdev:x:46:haldaemon,jim,janet,scheduled,kde
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,jim,janet,root,scheduled,kde
nvram:x:105:
ssl-cert:x:106:cupsys
crontab:x:107:
ssh:x:108:
avahi-autoipd:x:109:
messagebus:x:110:
avahi:x:111:
netdev:x:112:jim
lpadmin:x:113:jim
haldaemon:x:114:
powerdev:x:115:haldaemon,jim
slocate:x:116:
fuse:x:117:janet,scheduled,kde
jim:x:1000:
admin:x:118:jim,root,kde
gdm:x:119:
ntfs:x:1001:
boinc:x:120:
ntp:x:121:
janet:x:1002:
saned:x:122:
scheduled:x:1003:
vboxusers:x:1004:jim,root
kde:x:1005:
dirmngr:x:123:
```

[QUOTE=oldsoldier2003]or run
id
in a terminal to see what groups the account is assigned to.[/QUOTE]

```
jim@JIMJANET:~$ id
uid=1000(jim) gid=1000(jim) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),118(admin),1000(jim),1004(vboxusers)
jim@JIMJANET:~$ sudo id
[sudo] password for jim:
uid=0(root) gid=0(root) groups=0(root),20(dialout),24(cdrom),25(floppy),26(tape),29(audio),104(scanner),118(admin),1004(vboxusers)

```

---

### Post by bodhi.zazen on 2008-03-07
Do you have a separate partition for /home ? If so, is the partition mounted noexec ?

---

### Post by caughran on 2008-03-07
> **bodhi.zazen said:**
> Do you have a separate partition for /home ? If so, is the partition mounted noexec ?

Fstab entry is 

```
/dev/sda11 /home ext3 defaults,user 0 2
```

I just tried running one of the cron.daily scripts; it ran with no problem. But another try at a desktop script failed again, both for my id and for sudo. The /home and /jim and /Desktop folders seem to have full permission.

---

### Post by bodhi.zazen on 2008-03-07
The problem I assume is with noexec. 

The defaults for your home should be :

```
/dev/sda11 /home ext3 nodev,nosuid 0 2
```

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

You may need to add exec

> exec
    Permit execution of binaries.

```
/dev/sda11 /home ext3 nodev,exec 0 2
```

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Or move the script to / or /root and then run it from there.

---

### Post by caughran on 2008-03-07
Thanks. The nodev,nosuid 0 2 form worked.

---

