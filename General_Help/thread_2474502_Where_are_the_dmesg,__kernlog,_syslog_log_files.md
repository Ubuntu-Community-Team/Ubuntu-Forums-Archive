---
title: "Where are the dmesg,  kernlog, syslog log files?"
date: 2022-05-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2022-05-01
Ubuntu server 22.04

```
[FONT=monospace][COLOR=#000000]# ls /var/log [/COLOR]
alternatives.log       [COLOR=#5454ff]**apt**[/COLOR][COLOR=#000000]                    cloud-init.log  faillog         [/COLOR][COLOR=#5454ff]**libvirt**[/COLOR][COLOR=#000000]              wtmp [/COLOR]
alternatives.log.1     bootstrap.log          [COLOR=#5454ff]**dist-upgrade**[/COLOR][COLOR=#000000]    fontconfig.log  [/COLOR][COLOR=#5454ff]**mpd**[/COLOR]
[COLOR=#ff5454]**alternatives.log.2.gz**[/COLOR][COLOR=#000000]  btmp                   dpkg.log        [/COLOR][COLOR=#5454ff]**installer**[/COLOR][COLOR=#5454ff]**openvswitch**[/COLOR]
[COLOR=#5454ff]**apache2**[/COLOR][COLOR=#000000]                btmp.1                 dpkg.log.1      [/COLOR][COLOR=#5454ff]**journal**[/COLOR][COLOR=#5454ff]**private**[/COLOR]
apcupsd.events         cloud-init-output.log  [COLOR=#ff5454]**dpkg.log.2.gz**[/COLOR][COLOR=#000000]   lastlog         [/COLOR][COLOR=#5454ff]**unattended-upgrades**[/COLOR]
[/FONT]
```

noticed my server stopped working for a couple minutes this morning about 9AM and i wanted to check the logs files as it looked like it rebooted, crashed, reset, or lost power (unlikely with the power not going out and being on a UPS)

EDIT: was not a reboot, VM logs have no record of a clean shutdown

---

### Post by Doug S on 2022-05-01
Good question. I don't have them either (well, dmesg works fine). I assumed it was because I did a minimal install on the 22.04 server VM I created. I have not got around to trying a more normal install.

EDIT: I deleted my earlier VM and installed it again, but this time selecting the other option for install, the default one where humans are expected to login. The installation wasn't much bigger, 6.7G instead of 6.3G before. Now the expected log files are present:

```
doug@serv-jj:~$ ls -l /var/log
total 972
-rw-r--r--  1 root      root             27648 May  1 15:15 alternatives.log
drwxr-xr-x  2 root      root              4096 May  1 15:15 apt
-rw-r-----  1 syslog    adm               3833 May  1 15:15 [COLOR="#FF0000"]auth.log[/COLOR]
-rw-r--r--  1 root      root             64549 Apr 21 00:57 bootstrap.log
-rw-rw----  1 root      utmp                 0 Apr 21 00:57 btmp
-rw-r--r--  1 syslog    adm              90929 May  1 15:12 cloud-init.log
-rw-r-----  1 root      adm               4973 May  1 15:12 cloud-init-output.log
drwxr-xr-x  2 root      root              4096 Apr 18 17:47 dist-upgrade
-rw-r-----  1 root      adm              49078 May  1 15:12 dmesg
-rw-r--r--  1 root      root            517023 May  1 15:15 dpkg.log
-rw-r--r--  1 root      root             32032 May  1 15:12 faillog
drwxr-x---  3 root      adm               4096 May  1 15:11 installer
drwxr-sr-x+ 3 root      systemd-journal   4096 May  1 15:12 journal
-rw-r-----  1 syslog    adm              61357 May  1 15:14 [COLOR="#FF0000"]kern.log[/COLOR]
drwxr-xr-x  2 landscape landscape         4096 May  1 15:13 landscape
-rw-rw-r--  1 root      utmp            292292 May  1 15:14 lastlog
drwx------  2 root      root              4096 Apr 21 01:00 private
-rw-r-----  1 syslog    adm             109793 May  1 15:15 [COLOR="#FF0000"]syslog[/COLOR]
-rw-r--r--  1 root      root                 0 Apr 21 01:02 ubuntu-advantage.log
drwxr-x---  2 root      adm               4096 May  1 15:12 unattended-upgrades
-rw-rw-r--  1 root      utmp              2304 May  1 15:14 wtmp
```

---

### Post by philhughes on 2022-05-02
I do not have a server installation to check, but at a guess, journald is set to not forward logs to syslog. If you type:

```
systemd-analyze cat-config systemd/journald.conf
```

is #ForwardToSyslog=no?

You should be able to see your logs with:

```
journalctl
```

---

### Post by pqwoerituytrueiwoq on 2022-05-02
```
[FONT=monospace][COLOR=#5454ff]**# /etc/systemd/journald.conf**[/COLOR][COLOR=#000000] [/COLOR]
#  This file is part of systemd. 
# 
#  systemd is free software; you can redistribute it and/or modify it under the 
#  terms of the GNU Lesser General Public License as published by the Free 
#  Software Foundation; either version 2.1 of the License, or (at your option) 
#  any later version. 
# 
# Entries in this file show the compile time defaults. Local configuration 
# should be created by either modifying this file, or by creating "drop-ins" in 
# the journald.conf.d/ subdirectory. The latter is generally recommended. 
# Defaults can be restored by simply deleting this file and all drop-ins. 
# 
# Use 'systemd-analyze cat-config systemd/journald.conf' to display the full config. 
# 
# See journald.conf(5) for details. 

[Journal] 
#Storage=auto 
#Compress=yes 
#Seal=yes 
#SplitMode=uid 
#SyncIntervalSec=5m 
#RateLimitIntervalSec=30s 
#RateLimitBurst=10000 
#SystemMaxUse= 
#SystemKeepFree= 
#SystemMaxFileSize= 
#SystemMaxFiles=100 
#RuntimeMaxUse= 
#RuntimeKeepFree= 
#RuntimeMaxFileSize= 
#RuntimeMaxFiles=100 
#MaxRetentionSec= 
#MaxFileSec=1month 
#ForwardToSyslog=yes 
#ForwardToKMsg=no 
#ForwardToConsole=no 
#ForwardToWall=yes 
#TTYPath=/dev/console 
#MaxLevelStore=debug 
#MaxLevelSyslog=debug 
#MaxLevelKMsg=notice 
#MaxLevelConsole=info 
#MaxLevelWall=emerg 
#LineMax=48K 
#ReadKMsg=yes 
#Audit=no
[/FONT]
```

found the logs i think

[FONT=monospace][COLOR=#000000]```
May 01 12:13:21 niceServer systemd[99946]: Listening on GnuPG cryptographic agent (ssh-agent emulation). [/COLOR]
May 01 12:13:21 niceServer systemd[99946]: Listening on GnuPG cryptographic agent and passphrase cache. 
May 01 12:13:21 niceServer systemd[99946]: Listening on debconf communication socket. 
May 01 12:13:21 niceServer systemd[99946]: Listening on D-Bus User Message Bus Socket. 
May 01 12:13:21 niceServer systemd[99946]: Reached target Sockets. 
May 01 12:13:21 niceServer systemd[99946]: Reached target Basic System. 
May 01 12:13:21 niceServer systemd[99946]: Reached target Main User Target. 
May 01 12:13:21 niceServer systemd[99946]: Startup finished in 517ms. 
May 01 12:13:21 niceServer systemd[1]: Started User Manager for UID 1000. 
May 01 12:13:21 niceServer systemd[1]: Started Session 112 of User chad. 
May 01 12:13:32 niceServer sudo[99983]: [COLOR=#000000]**    chad : TTY=pts/1 ; PWD=/home/chad ; USER=root ; COMMAND=/usr/bin/nano /etc/netplan/00-installer-config.yaml**[/COLOR][COLOR=#000000] [/COLOR]
May 01 12:13:32 niceServer sudo[99983]: pam_unix(sudo:session): session opened for user root(uid=0) by chad(uid=1000) 
May 01 12:16:53 niceServer sshd[100145]: Accepted publickey for chad from 10.0.0.50 port 56610 ssh2: RSA SHA256:D3yZeQeeCjri+tjL//8xQj8g7+9vT284e8nY/6OVOOs 
May 01 12:16:53 niceServer sshd[100145]: pam_unix(sshd:session): session opened for user chad(uid=1000) by (uid=0) 
May 01 12:16:53 niceServer systemd-logind[697]: New session 114 of user chad. 
May 01 12:16:53 niceServer systemd[1]: Started Session 114 of User chad. 
May 01 12:16:57 niceServer polkitd(authority=local)[2777]: [COLOR=#000000]**Registered Authentication Agent for unix-process:100176:12125595 (system bus name :1.46 [/usr/bin/pkttyagent --process 100176 --notify-fd 4 --fallback], object path /org/freedes**[/COLOR][COLOR=#ffffff]>[/COLOR][COLOR=#000000] [/COLOR]
May 01 12:16:57 niceServer polkitd(authority=local)[2777]: [COLOR=#000000]**Unregistered Authentication Agent for unix-process:100176:12125595 (system bus name :1.46, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale C.UTF-8) (disconne**[/COLOR][COLOR=#ffffff]>[/COLOR][COLOR=#000000] [/COLOR]
May 01 12:17:01 niceServer CRON[100183]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0) 
May 01 12:17:01 niceServer CRON[100184]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly) 
May 01 12:17:01 niceServer CRON[100183]: pam_unix(cron:session): session closed for user root 
May 01 12:17:29 niceServer polkitd(authority=local)[2777]: [COLOR=#000000]**Registered Authentication Agent for unix-process:100208:12128787 (system bus name :1.47 [/usr/bin/pkttyagent --process 100208 --notify-fd 4 --fallback], object path /org/freedes**[/COLOR][COLOR=#ffffff]>[/COLOR][COLOR=#000000] [/COLOR]
May 01 12:17:29 niceServer polkitd(authority=local)[2777]: [COLOR=#000000]**Unregistered Authentication Agent for unix-process:100208:12128787 (system bus name :1.47, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale C.UTF-8) (disconne**[/COLOR][COLOR=#ffffff]>[/COLOR][COLOR=#000000] [/COLOR]
May 01 12:19:24 niceServer sudo[99983]: pam_unix(sudo:session): session closed for user root 
May 01 12:30:42 niceServer systemd[1]: run-docker-runtime\x2drunc-moby-54f306685896e4334eb2f719e10d78f37512ae949b943ff69072a63f8e5b3c10-runc.GSN8Fh.mount: Deactivated successfully. 
May 01 12:39:01 niceServer CRON[101197]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0) 
May 01 12:39:01 niceServer CRON[101198]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi) 
May 01 12:39:01 niceServer CRON[101197]: pam_unix(cron:session): session closed for user root 
May 01 12:39:15 niceServer systemd[1]: Starting Clean php session files... 
May 01 12:39:16 niceServer systemd[1]: phpsessionclean.service: Deactivated successfully. 
May 01 12:39:16 niceServer systemd[1]: Finished Clean php session files. 
May 01 12:42:48 niceServer systemd[1]: Starting Daily apt download activities... 
May 01 12:42:56 niceServer systemd[1]: apt-daily.service: Deactivated successfully. 
May 01 12:42:56 niceServer systemd[1]: Finished Daily apt download activities. 
May 01 12:42:56 niceServer systemd[1]: apt-daily.service: Consumed 5.958s CPU time. 
[COLOR=#000000]**-- Boot b91a17a111fc471f9f57d32e363f4427 --**[/COLOR][COLOR=#000000] [/COLOR]
May 01 13:00:16 niceServer kernel: [COLOR=#000000]**Linux version 5.15.0-27-generic (buildd@ubuntu) (gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 (Ubuntu 5.15.0-27.28-generic 5.**[/COLOR][COLOR=#ffffff]>[/COLOR][COLOR=#000000] [/COLOR]
May 01 13:00:16 niceServer kernel: Command line: BOOT_IMAGE=/vmlinuz-5.15.0-27-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro amd_iommu=on iommu=pt 
May 01 13:00:16 niceServer kernel: KERNEL supported cpus: 
May 01 13:00:16 niceServer kernel:   Intel GenuineIntel 
May 01 13:00:16 niceServer kernel:   AMD AuthenticAMD 
May 01 13:00:16 niceServer kernel:   Hygon HygonGenuine 
May 01 13:00:16 niceServer kernel:   Centaur CentaurHauls 
May 01 13:00:16 niceServer kernel:   zhaoxin   Shanghai   
May 01 13:00:16 niceServer kernel: x86/fpu: x87 FPU will use FXSAVE
```

i think i need to set the time zone for my own sanity

no errors or anything, it did not seem like the +12v was lost on the system as power was not lost on my modem (my PSU is also powering a switch and a cable modem) so it was not a full power cycle

maybe it was a bad reading on the case reset switch?
[/FONT]

---

