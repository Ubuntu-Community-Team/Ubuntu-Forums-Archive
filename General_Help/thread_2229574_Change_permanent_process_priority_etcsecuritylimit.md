---
title: "Change permanent process priority /etc/security/limits.conf /etc/rc2.d"
date: 2014-06-13
forum: General Help
---

### Post by Andrew F in Australia on 2014-06-13
HI All,

I've got a computer dedicated as a music server.

It runs logitech squeeze centre, using the deb file from here:
[http://downloads.slimdevices.com/nightly/?ver=7.8](http://downloads.slimdevices.com/nightly/?ver=7.8)

Recently (the last six months or so,) it has taken about 2 minutes or more for the program to open once the system boots into linux.  More a frustation than anything else as it does work well once started.

I've tried to raise the priority of the squeezeboxserver user that this program runs under by editing the /etc/security/limits.conf file as outlined here:
[http://linux.die.net/man/5/limits.conf](http://linux.die.net/man/5/limits.conf)

Still no luck:





```
login@horacemusic-GA-970A-D3:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:111:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:107:113:RealtimeKit,,,:/proc:/bin/false
whoopsie:x:108:114::/nonexistent:/bin/false
speech-dispatcher:x:109:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi:x:110:116:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:111:117:Light Display Manager:/var/lib/lightdm:/bin/false
pulse:x:112:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
colord:x:114:122:colord colour management daemon,,,:/var/lib/colord:/bin/false
saned:x:115:123::/home/saned:/bin/false
horace-music:x:1000:1000:horace-music,,,:/home/horace-music:/bin/bash
squeezeboxserver:x:116:65534:Logitech Media Server,,,:/usr/share/squeezeboxserver:/bin/false
login:x:1001:1001:login,,,:/home/login:/bin/bash
login@horacemusic-GA-970A-D3:~$ 


```
```

login@horacemusic-GA-970A-D3:~$ top -u squeezeboxserver

top - 10:18:32 up 2 min,  2 users,  load average: 0.70, 0.52, 0.21
Tasks: 220 total,   2 running, 218 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.0 us,  2.0 sy,  0.0 ni, 95.8 id,  0.1 wa,  0.1 hi,  0.0 si,  0.0 st
KiB Mem:  16415552 total,  1180056 used, 15235496 free,    83028 buffers
KiB Swap: 16756732 total,        0 used, 16756732 free.   441388 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1199 squeeze+  20   0  252312 144996   5252 S   0.3  0.9   0:02.70 squeezebox+ 
 1152 squeeze+  20   0   17972   1548   1288 S   0.0  0.0   0:00.00 squeezebox+ 


```

Also tried to change the run order of the processes by editing the /etc/rc2.d file (the 'who -r' ccommand gave this as the operating directory), as detailed here:
[http://smallbusiness.chron.com/change-start-order-processes-linux-61730.html](http://smallbusiness.chron.com/change-start-order-processes-linux-61730.html)

No luck either way, it still ran as a default priority user

Could anybody point out where I've gone wrong?

Thanks in advance,

Andrew F

---

### Post by alexandari on 2014-06-14
I see that the file limits.conf works with **[COLOR="#000000"]nice[/COLOR]** and so on
If you wanna change a process priority,you can use the command **nice**,or **renice**
If the process is already running,and you want to give it a low priority,try this

```
 sudo renice 10 -p PID 
```

for a higher one

```
 sudo renice -10 -p PID 
```

they go from -20 to 19

lower number = higher priority

check out if this changes the priority,the console will produce an output

---

### Post by Andrew F in Australia on 2014-06-14
Thanks Alexandari,

I edited the limits.conf file with a command like

username (tab) soft (tab) priority (tab) -5
Saved and rebooted,
No change to the running priority.  
nice/renice commands worked well when run in a terminal and had the desired effect but...

Is there a way to set this on startup, rather than having to go into a terminal each time and reset priority?

With this /etc/security/limits.conf file
```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - a user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
squeezeboxserver    soft    priority    -10
squeezeboxserver    soft    nice    -9
horace-music    hard    priority    2
# End of file

```

I get this output: (hard or soft limits worked identically)
```
top - 06:26:57 up 1 min,  2 users,  load average: 1.45, 0.49, 0.17
Tasks: 229 total,   2 running, 226 sleeping,   0 stopped,   1 zombie
%Cpu(s):  1.0 us,  1.5 sy,  0.0 ni, 79.5 id, 17.8 wa,  0.2 hi,  0.0 si,  0.0 st
KiB Mem:  16415552 total,  1210928 used, 15204624 free,    96884 buffers
KiB Swap: 16756732 total,        0 used, 16756732 free.   469688 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1239 squeeze+  20   0  241328 135672   4904 D   2.3  0.8   0:02.16 squeezebox+ 
 1159 squeeze+  20   0   17972   1544   1288 S   0.0  0.0   0:00.00 squeezebox+
```
Regards,

AF

---

### Post by alexandari on 2014-06-14
A workaround to this is to set up the system to execute the command at startup (I'm talking about nice/renice). You can put your command in **/etc/rc.local**

---

### Post by Andrew F in Australia on 2014-06-14
Thanks Alexandari,

I'll figure it out tonight from there.  Brilliant - thanks for the input.

I'll post tomorrow and let you know how it went.

AF

---

