---
title: "I blew up a module, how to fix?"
date: 2006-11-17
forum: General Help
---

### Post by Duffy on 2006-11-17
Group, I don't know what the heck I did, but I tried to change the name of an existing user in Kubuntu to a new name, and now the freakin' User Management no longer works. Gives an error "The module User Management could not be loaded."

Anyone give me a clue as to how to fix this?

Thanks,

Duffy

p.s. Also, if someone can tell me how to change the name of the default user directory I would appreciate it. The default was "kubuntu" and I want to give it the same name as the user name I changed. The original user name was "kubuntu" which I changed to "tom" and I thought that would change the directory name also, but it does not. So I have everything kindof hosed right now, but it is still working, except for user management.

---

### Post by David_T on 2006-11-17
Could you post the output of the following commands?:

cat /etc/passwd
ls /home


You might also want to look at the man page for the usermod command, which has an option to change a user's home directory.

---

### Post by Duffy on 2006-11-18
Thanks, I will give that a try as soon as I can get some help as to how to restore the user management module.

---

### Post by Duffy on 2006-11-19
As requested:

cat /etc/passwd:
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
cupsys:x:100:106::/home/cupsys:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
WB8NUT:x:1000:100:Amateur Radio WB8NUT:/home/kubuntu:/bin/bash
avahi:x:106:113:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
WB8NUT@kubuntu-desktop:~$  

ls /home:
kubuntu

---

### Post by Duffy on 2006-12-08
Wow, no one knows how to fix? Well nevermind, I blew off the installation and did another reinstall. I wish Linux had a feature like Windoz where you can put in the CD and tell it to repair the installation. Saves the time of reinstall and setting everything up again.

---

