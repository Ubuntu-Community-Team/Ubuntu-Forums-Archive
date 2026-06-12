---
title: "[SOLVED] How to rescue broken system ubuntu – solved"
date: 2008-03-04
forum: General Help
---

### Post by bole on 2008-03-04
Since I didn't find enough online help to solve my problem, I will explain how I broke my ubuntu and how I solved it for future reference.
After almost one year using the community's help I would like to give back as much as possible to support free software projects and the beautiful cooperation idea that is behind them.

Hardware: hp compaq 6515b  AMD 64

Software: Ubuntu 7.10 64 bits

Problem description:
Impossible to start ubuntu. System information:
sulogin: cannot open password database!
segmentation fault
init: rcS-sulogin main process (4975) terminated with status 139

That means that it is impossible to login into the system because it does not recognize any user nor password, including root.

Why? Probably because there is some problem in the files managing this username/password. Those files are:
/etc/passwd (it contains the list of users -not only real «persons» but also some needed for some processes) and system information about them. 
/etc/shadow    (it contains the password in an encrypted form)

Problem cause: 
After some research I found out the root problem was that an installation of SAGE (a mathematical program) – intallation from their website, not from repositories – had stepped on some files on my system. One of those destroyed files been /etc/passwd !!

Note: actually, it is not the first time that i get this problem description.
The previous time root cause was not really defined but i understood that there had been some data corruption because my system experienced a power black out while in the middle of the shuting down process.
That time I just took out some important data from my ubuntu partition using Windows based tools for reading ext3, from my Windows partition.

Solution:
I tried to access the system with DMS (Damm Small Linux) but I had problems for mounting the filesystem. Most probably because of lack of knownledge, not because of system problems.

I used the «Rescue System» mode of my Ubuntu Installation CD. No problem even if it was for 7.4 and was not the Live CD version, but the Alternate one.

Throug this rescue system option, I gained a terminal as root.
file /etc/passwd tell me that it was a .png file! 

After studying the /etc/passwd format 

[username:password:userID:groupID:gecos:homedirectory:bash]

I created with vi a new /etc/passwd containing the minimum information for being able to login.
My /etc/passwd was:
root:x:0:0::/root:/bin/bash
pablo:x:1000:1000::/home/pablo:/bin/bash

After restoring in this way my /etc/passwd I was able to reboot the computer without system errors and was able to login as pablo.

Anyhow, I was only able to work in text mode because I was getting the following message:
GDM user 'gdm' does not exist.
Please correct GDM configuration and restart GDM.

With the startx command I was able to get a working Gnome but still had some error messages as: Failed to initialize HAL!

Also, cd or usbkeys were not being automatically mounted.

It was clear then that my /etc/passwd file was far away from being complete.
Hopefully I have another machine running also ubuntu (dell 32bits).
So I more or less (different main users, some programs like apache running only on one machine...) copied the /etc/passed on the dell machine to the one of the hp machine.

I finally got everything running correctly.

I will copy here my /etc/passwd for your reference of which users and daemons need to be running:

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news/:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:100::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:106::/var/run/dbus:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
cupsys:x:106:113::/home/cupsys:/bin/false
haldaemon:x:107:114:Hardware abstaction layer,,,:/home/haldaemon:/bin/false
hplip:x:108:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:109:118:GDM User:/var/lib/gdm:/bin/false
pablo:x:1000:1000::/home/pablo:/bin/bash
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
dictd:x:111:123::/var/lib/dictd:/bin/false

Hope that was useful.

---

### Post by talsemgeest on 2008-03-04
BTW to mark the thread as solved go to thread tools and "mark thread as solved"

---

### Post by erginemr on 2008-03-04
Thank you for sharing your experience and solution you have found with other forum members.

*Ubuntu = I am what I am because of who we all are. *

---

### Post by bole on 2008-03-05
Thanks for your tip, talsemgeest. Still, a long way to learn!

---

### Post by talsemgeest on 2008-03-05
Always nice to help. And good on ya for sharing your experience with others

---

