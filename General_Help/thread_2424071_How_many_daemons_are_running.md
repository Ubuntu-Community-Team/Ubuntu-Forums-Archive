---
title: "How many daemons are running?"
date: 2019-08-02
forum: General Help
---

### Post by Artim on 2019-08-02
How can I tell how many daemons are running?  I read that Ubuntu has an unbelievable [SIZE=5]90[/SIZE] daemons running after startup!  I guess Xubuntu has fewer, and I uncheck startup services and stuff in the startup menu, but I'd like to minimize the number of things running in the background.  Is there a quick way to tell how many and which ones I don't really need (like Bluetooth, for example)?

---

### Post by TheFu on 2019-08-02
Not that I know.  Not all daemons are centrally controlled.  Any userid on the system can run one.
You can see which are impacting boot times using **systemd-analyze blame**.
For more information on that command (or any other commands on your specific system), check out the manpage which will provide more options with an explanation of each.

Also, the number of programs started will depend on the specific release, the specific hardware, the specific file systems used, and a multitude of installation options.  Did you choose encryption?  Did you choose to have LVM?  Are you using ZFS?  Did you install any servers like apache, nginx, ssh, redis, mariadb, postgres, postfix, inn, zcs, znc, plex, or any of 5,000 others?

If you look in /etc/init/ and /etc/init.d/ you can see some of the startup and shutdown configuration files.  Systemd has startup and shutdown dependency config files stored elsewhere in the systemd -specific way.

---

### Post by Artim on 2019-08-03
Great info!  Thanks!

---

### Post by Doug S on 2019-08-03
To see how many threads (not all would be daemons) are running (or sleeping) just use top and it'll tell you, right on the second line:

```
top - 08:24:06 up 14:53,  6 users,  load average: 0.01, 0.00, 0.00
Tasks: [COLOR="#FF0000"]172 total,   1 running,  95 sleeping[/COLOR],   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16121628 total, 11718676 free,   141796 used,  4261156 buff/cache
KiB Swap: 16472060 total, 16468464 free,     3596 used. 15544040 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 6060 doug      20   0   41796   3720   3084 R   0.3  0.0   0:00.08 top
    1 root      20   0   37992   5988   3984 S   0.0  0.0   0:05.04 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_gp

```The above was for a server. This is a desktop:
```
top - 08:26:21 up 35 days, 25 min,  2 users,  load average: 1.24, 0.37, 0.12
Tasks: [COLOR="#FF0000"]233 total,   1 running, 190 sleeping,[/COLOR]   0 stopped,   0 zombie
%Cpu0  :  1.0 us,  0.7 sy,  0.0 ni, 98.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  1.0 us,  0.3 sy,  0.0 ni, 98.0 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  2038032 total,   143644 free,  1017080 used,   877308 buff/cache
KiB Swap:  2097148 total,  1283184 free,   813964 used.   831520 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1053 gdm       20   0  967796  14820   3900 S   0.7  0.7 183:57.57 gsd-color
 1480 doug      20   0  677772  14476   3480 S   0.7  0.7 185:04.24 gsd-color
23916 doug      20   0   51316   4292   3552 R   0.7  0.2   0:00.14 top
 2157 doug      20   0 1694756  61432  13396 S   0.3  3.0  42:08.06 Web Content

```but like TheFu said, it depends.

---

### Post by TheFu on 2019-08-03
```
top - 12:40:19 up  1:40,  1 user,  load average: 0.01, 0.04, 0.03
Tasks:  98 total,   1 running,  65 sleeping,   0 stopped,   0 zombie

```
That is a desktop, before any GUI session is started. I ssh'd in.

Here's a server:
```
top - 12:42:16 up  1:42,  1 user,  load average: 0.01, 0.02, 0.05
Tasks:  74 total,   1 running,  73 sleeping,   0 stopped,   0 zombie
```

I patched and reboot them all this morning, so they are pretty clean running now.

My main VM host server:
```
top - 12:43:35 up  1:44,  1 user,  load average: 0.12, 0.25, 0.27
Tasks: 293 total,   1 running, 166 sleeping,   0 stopped,   0 zombie

```
All of these didn't have a GUI login. I ssh'd in.

---

### Post by Artim on 2019-08-03
Top says **1 running, 127 sleeping** (that's with one tab in Seamonkey open, terminal, Xfce desktop and network manager running.  My gosh that's a lot of sleeping processes!  It's not using much CPU and I'm not "having an issue," I was just curious about optimizing my OS.  It looks like I can with all those sleeping processes, but it's not causing any slowdown or anything, nor using much CPU or RAM.

---

