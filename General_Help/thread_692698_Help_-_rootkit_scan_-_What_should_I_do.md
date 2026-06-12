---
title: "Help - rootkit scan - What should I do?"
date: 2008-02-10
forum: General Help
---

### Post by ubuntu27 on 2008-02-10
I just did a Rootkit scan with chkrootkit and I had positive result, it found nothing.

But when I scanned using **rkhunter**, it shoed some peculiar results. 

> ubuntu27@crunch:~$ su
Password:
erai:/home/ubuntu27# rkhunter -c
[ Rootkit Hunter version 1.3.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 **[ Warning ]**
    /bin/chmod                                               **[ Warning ]**
    /bin/chown                                               **[ Warning ]**
    /bin/cp                                                  **[ Warning ]**
    /bin/csh                                                 [ OK ]
    /bin/date                                                **[ Warning ]**
    /bin/df                                                  **[ Warning ]**
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                **[ Warning ]**
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                **[ Warning ]**
    /bin/login                                               [ OK ]
    /bin/ls                                                  **[ Warning ]**
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ Warning ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ Warning ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 **[ Warning ]**
    /bin/readlink                                            **[ Warning ]**
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ Warning ]
    /bin/uname                                               **[ Warning ]**
    /bin/which                                               [ OK ]
    /bin/tcsh                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        **[ Warning ]**
    /usr/bin/chattr                                          **[ Warning ]**
    /usr/bin/cut                                             **[ Warning ]**
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ Warning ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ Warning ]
    /usr/bin/env                                             [ Warning ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ Warning ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ Warning ]
    /usr/bin/head                                            [ Warning ]
    /usr/bin/id                                              [ Warning ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            **[ Warning ]**
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          **[ Warning ]**
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          **[ Warning ]**
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          **[ Warning ]**
    /usr/bin/sha1sum                                         [ Warning ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            **[ Warning ]**
    /usr/bin/stat                                            **[ Warning ]**
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            **[ Warning ]**
    /usr/bin/tail                                            **[ Warning ]**
    /usr/bin/test                                            **[ Warning ]**
    /usr/bin/top                                             **[ Warning ]**
    /usr/bin/touch                                           **[ Warning ]**
    /usr/bin/tr                                              **[ Warning ]**
    /usr/bin/uniq                                            **[ Warning ]**
    /usr/bin/users                                           **[ Warning ]**
    /usr/bin/vmstat                                          **[ Warning ]**
    /usr/bin/w                                               **[ Warning ]**
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              **[ Warning ]**
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          **[ Warning ]**
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             **[ Warning ]**
    /usr/bin/whoami                                          **[ Warning ]**
    /usr/bin/tcsh                                            [ OK ]
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        **[ Warning ]**
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               **[ Warning ]**
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           **[ Warning ]**
    /sbin/sulogin                                            **[ Warning ]**
    /sbin/sysctl                                             [ Warning ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         **[ Warning ]**
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/inetd                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/sestatus                                       **[ Warning ]**
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         **[ Warning ]**
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 **[ Warning ]**


Should I be concerned about those "Warnings" ?

There are more:

> Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      **[ Warning ]**

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]


> Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                **[ Warning ]**


System checks summary
=====================

File properties checks...
    Files checked: 128
    Suspect files: 59

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 4
    Suspect applications: 0

The system checks took: 8 minutes and 19 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)



What should I do now? how can I know that something is wrong?
I am new to rootkit ><

---

### Post by dcstar on 2008-02-10
> **ubuntu27 said:**
> I just did a Rootkit scan with chkrootkit and I had positive result, it found nothing.

But when I scanned using **rkhunter**, it shoed some peculiar results. 
..............
One or more warnings have been found while checking the system.
**Please check the log file (/var/log/rkhunter.log)**



What should I do now? how can I know that something is wrong?
I am new to rootkit ><

Following that specific advice would be a good start.

---

### Post by Nepherte on 2008-02-10
I have similar warnings and the log file always states that it is replaced by another script. I guess that's the same case for you. Don't think you have to worry about that because I had those warnings on a clean ubuntu install.

---

### Post by ubuntu27 on 2008-02-10
This is what's in the log:

I used ```
cat /var/log/rkhunter.log
```


> [10:12:47] Warning: The file properties have changed:
[10:12:47]          File: /usr/bin/tail
[10:12:47]          Current inode: 2621590    Stored inode: 2621654
[10:12:48]          Current file modification time: 1201575835
[10:12:48]          Stored file modification time : 1201139085
[10:12:48] /usr/bin/test                                     [ Warning ]
[10:12:48] Warning: The file properties have changed:
[10:12:48]          File: /usr/bin/test
[10:12:48]          Current inode: 2621691    Stored inode: 2621677
[10:12:48]          Current file modification time: 1201575835
[10:12:48]          Stored file modification time : 1201139085
[10:12:48] /usr/bin/top                                      [ Warning ]
[10:12:48] Warning: The file properties have changed:
[10:12:48]          File: /usr/bin/top
[10:12:49]          Current hash: ee0cf237cb1f4df36c7af0fe5387bc3493e8dafd
[10:12:49]          Stored hash : cda0b37e1613435c029b82a3a70ebdecc1d27ae6
[10:12:49]          Current inode: 4215845    Stored inode: 4213927
[10:12:49]          Current size: 50160    Stored size: 52272
[10:12:49]          Current file modification time: 1201867354
[10:12:49]          Stored file modification time : 1191589008
[10:12:49] /usr/bin/touch                                    [ Warning ]
[10:12:49] Warning: The file properties have changed:
[10:12:49]          File: /usr/bin/touch
[10:12:49]          Current inode: 2621683    Stored inode: 2621685
[10:12:49]          Current file modification time: 1201646871
[10:12:49]          Stored file modification time : 1201228552
[10:12:49] /usr/bin/tr                                       [ Warning ]
[10:12:50] Warning: The file properties have changed:
[10:12:50]          File: /usr/bin/tr
[10:12:50]          Current inode: 2621591    Stored inode: 2621655
[10:12:50]          Current file modification time: 1201575835
[10:12:50]          Stored file modification time : 1201139085
[10:12:50] /usr/bin/uniq                                     [ Warning ]
[10:12:50] Warning: The file properties have changed:
[10:12:50]          File: /usr/bin/uniq
[10:12:50]          Current inode: 2621594    Stored inode: 2621658
[10:12:50]          Current file modification time: 1201575835
[10:12:50]          Stored file modification time : 1201139085
[10:12:51] /usr/bin/users                                    [ Warning ]
[10:12:51] Warning: The file properties have changed:
[10:12:51]          File: /usr/bin/users
[10:12:51]          Current inode: 2621542    Stored inode: 2621605
[10:12:51]          Current file modification time: 1201575834
[10:12:51]          Stored file modification time : 1201139085
[10:12:51] /usr/bin/vmstat                                   [ Warning ]
[10:12:51] Warning: The file properties have changed:
[10:12:51]          File: /usr/bin/vmstat
[10:12:51]          Current hash: 44a7c53a6601ec81194c4123ac725b66e205de32
[10:12:51]          Stored hash : 60e36149ffd61f29429e1e2bbf89c46e263e8c53
[10:12:51]          Current inode: 4215872    Stored inode: 4213928
[10:12:51]          Current size: 18352    Stored size: 18368
[10:12:51]          Current file modification time: 1201867354
[10:12:51]          Stored file modification time : 1191589008
[10:12:52] /usr/bin/w                                        [ Warning ]
[10:12:52] Warning: The file properties have changed:
[10:12:52]          File: /usr/bin/w
[10:12:52]          Current hash: 5ba8d0f9dd83f13c16ec3e4ddfa1062cf07af6d6
[10:12:52]          Stored hash : 7aa9d967a2f89a061d45f6149985a811c8b6803d
[10:12:52] /usr/bin/watch                                    [ Warning ]
[10:12:52] Warning: The file properties have changed:
[10:12:52]          File: /usr/bin/watch
[10:12:52]          Current hash: 3f0ec1c7f42eda4819cf1c7a5c745e732ff80729
[10:12:52]          Stored hash : 72010bee3b4c81fd08fabc7e97418c1db77301cb
[10:12:52]          Current inode: 4215873    Stored inode: 4213929
[10:12:52]          Current size: 9136    Stored size: 9200
[10:12:52]          Current file modification time: 1201867354
[10:12:53]          Stored file modification time : 1191589008
[10:12:53] /usr/bin/wc                                       [ Warning ]
[10:12:53] Warning: The file properties have changed:
[10:12:53]          File: /usr/bin/wc
[10:12:53]          Current inode: 2621595    Stored inode: 2621659
[10:12:53]          Current file modification time: 1201575835
[10:12:53]          Stored file modification time : 1201139085
[10:12:53] /usr/bin/wget                                     [ OK ]
[10:12:54] /usr/bin/whatis                                   [ Warning ]
[10:12:54] Warning: The file properties have changed:
[10:12:54]          File: /usr/bin/whatis
[10:12:54]          Current hash: 78685f713eb7608ae57f6897ae5628aaad332ed6
[10:12:54]          Stored hash : fd8945aac9aba1c24002c5ad29bcebc7beab0034
[10:12:54]          Current inode: 4219307    Stored inode: 4219805
[10:12:54]          Current size: 87276    Stored size: 60296
[10:12:54]          Current file modification time: 1201563557
[10:12:54]          Stored file modification time : 1195329862
[10:12:54] /usr/bin/whereis                                  [ OK ]
[10:12:55] /usr/bin/which                                    [ OK ]
[10:12:55] /usr/bin/who                                      [ Warning ]
[10:12:55] Warning: The file properties have changed:
[10:12:55]          File: /usr/bin/who
[10:12:55]          Current inode: 2621541    Stored inode: 2621604
[10:12:55]          Current file modification time: 1201575834
[10:12:55]          Stored file modification time : 1201139085
[10:12:55] /usr/bin/whoami                                   [ Warning ]
[10:12:55] Warning: The file properties have changed:
[10:12:56]          File: /usr/bin/whoami
[10:12:56]          Current inode: 2621693    Stored inode: 2621679
[10:12:56]          Current file modification time: 1201575835
[10:12:56]          Stored file modification time : 1201139085
[10:12:56] /usr/bin/tcsh                                     [ OK ]
[10:12:56] /usr/bin/gawk                                     [ OK ]
[10:12:57] /usr/bin/lwp-request                              [ OK ]
[10:12:57] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[10:12:57] /usr/bin/bsd-mailx                                [ OK ]
[10:12:57] /usr/bin/w.procps                                 [ Warning ]
[10:12:57] Warning: The file properties have changed:
[10:12:58]          File: /usr/bin/w.procps
[10:12:58]          Current hash: 5ba8d0f9dd83f13c16ec3e4ddfa1062cf07af6d6
[10:12:58]          Stored hash : 7aa9d967a2f89a061d45f6149985a811c8b6803d
[10:12:58]          Current inode: 4216864    Stored inode: 4213935
[10:12:58]          Current file modification time: 1201867354
[10:12:58]          Stored file modification time : 1191589008
[10:12:59] /sbin/depmod                                      [ OK ]
[10:13:00] /sbin/ifconfig                                    [ OK ]
[10:13:00] /sbin/ifdown                                      [ OK ]
[10:13:00] /sbin/ifup                                        [ OK ]
[10:13:01] /sbin/init                                        [ Warning ]
[10:13:01] Warning: The file properties have changed:
[10:13:01]          File: /sbin/init
[10:13:01]          Current inode: 327777    Stored inode: 327697
[10:13:01]          Current file modification time: 1201891119
[10:13:01]          Stored file modification time : 1200842280
[10:13:01] /sbin/insmod                                      [ OK ]
[10:13:02] /sbin/ip                                          [ OK ]
[10:13:02] /sbin/lsmod                                       [ OK ]
[10:13:03] /sbin/modinfo                                     [ OK ]
[10:13:03] /sbin/modprobe                                    [ OK ]
[10:13:04] /sbin/rmmod                                       [ OK ]
[10:13:04] /sbin/runlevel                                    [ Warning ]
[10:13:04] Warning: The file properties have changed:
[10:13:04]          File: /sbin/runlevel
[10:13:04]          Current inode: 327870    Stored inode: 327863
[10:13:04]          Current file modification time: 1201891119
[10:13:04]          Stored file modification time : 1200842280
[10:13:05] /sbin/sulogin                                     [ Warning ]
[10:13:05] Warning: The file properties have changed:
[10:13:05]          File: /sbin/sulogin
[10:13:05]          Current inode: 327697    Stored inode: 327682
[10:13:05]          Current file modification time: 1201891165
[10:13:05]          Stored file modification time : 1200842282
[10:13:05] /sbin/sysctl                                      [ Warning ]
[10:13:05] Warning: The file properties have changed:
[10:13:06]          File: /sbin/sysctl
[10:13:06]          Current hash: 21925fe472f43b993a23064899ca3dd2a4145d3f
[10:13:06]          Stored hash : 7170fc67dbe417b319dda3464b6b1b421ff3e115
[10:13:06]          Current inode: 327700    Stored inode: 327770
[10:13:06]          Current file modification time: 1201867354
[10:13:06]          Stored file modification time : 1191589008
[10:13:06] /sbin/syslogd                                     [ OK ]
[10:13:07] /usr/sbin/adduser                                 [ OK ]
[10:13:07] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[10:13:07] /usr/sbin/chroot                                  [ Warning ]
[10:13:07] Warning: The file properties have changed:
[10:13:07]          File: /usr/sbin/chroot
[10:13:07]          Current inode: 2818051    Stored inode: 2818080
[10:13:07]          Current file modification time: 1201575835
[10:13:07]          Stored file modification time : 1201139085
[10:13:08] /usr/sbin/cron                                    [ OK ]
[10:13:08] /usr/sbin/groupadd                                [ OK ]
[10:13:08] /usr/sbin/groupdel                                [ OK ]
[10:13:09] /usr/sbin/groupmod                                [ OK ]
[10:13:09] /usr/sbin/grpck                                   [ OK ]
[10:13:09] /usr/sbin/inetd                                   [ OK ]
[10:13:10] /usr/sbin/nologin                                 [ OK ]
[10:13:10] /usr/sbin/pwck                                    [ OK ]
[10:13:11] /usr/sbin/sestatus                                [ Warning ]
[10:13:11] Warning: The file properties have changed:
[10:13:11]          File: /usr/sbin/sestatus
[10:13:11]          Current hash: 64760b405b068fb555029ef05cb13202a077dd6c
[10:13:11]          Stored hash : 22d8eb0e246cfd055b715fe1334f7ec986ae57a0
[10:13:11]          Current inode: 4217583    Stored inode: 4215347
[10:13:11]          Current size: 9232    Stored size: 8916
[10:13:11]          Current file modification time: 1202337397
[10:13:11]          Stored file modification time : 1178518603
[10:13:12] /usr/sbin/tcpd                                    [ OK ]
[10:13:12] /usr/sbin/unhide                                  [ Warning ]
[10:13:12] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[10:13:12] /usr/sbin/useradd                                 [ OK ]
[10:13:12] /usr/sbin/userdel                                 [ OK ]
[10:13:13] /usr/sbin/usermod                                 [ OK ]
[10:13:13] /usr/sbin/vipw                                    [ OK ]
[10:13:13] /usr/sbin/unhide-linux26                          [ Warning ]
[10:13:13] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[10:13:17]
[10:13:17] Checking for rootkits...
[10:13:18] Info: Starting test name 'rootkits'
[10:13:18]
[10:13:18] Performing check of known rootkit files and directories
[10:13:18] Info: Starting test name 'known_rkts'
[10:13:18]
[10:13:18] Checking for 55808 Trojan - Variant A...
[10:13:18]   Checking for file '/tmp/.../r'                  [ Not found ]
[10:13:18]   Checking for file '/tmp/.../a'                  [ Not found ]
[10:13:18] 55808 Trojan - Variant A                          [ Not found ]
[10:13:18]
[10:13:18] Checking for ADM Worm...
[10:13:18]   Checking for string 'w0rm'                      [ Not found ]
[10:13:18] ADM Worm                                          [ Not found ]
[10:13:18]
[10:13:18] Checking for AjaKit Rootkit...
[10:13:18]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:13:18]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:13:18]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:13:19]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[10:13:19]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[10:13:19]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[10:13:19]   Checking for directory '/dev/tux'               [ Not found ]
[10:13:19]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[10:13:19] AjaKit Rootkit                                    [ Not found ]
[10:13:19]
[10:13:19] Checking for aPa Kit...
[10:13:19]   Checking for file '/usr/share/.aPa'             [ Not found ]
[10:13:19] aPa Kit                                           [ Not found ]
[10:13:19]
[10:13:19] Checking for Apache Worm...
[10:13:19]   Checking for file '/bin/.log'                   [ Not found ]
[10:13:19] Apache Worm                                       [ Not found ]
[10:13:20]
[10:13:20] Checking for Ambient (ark) Rootkit...
[10:13:20]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[10:13:20]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[10:13:20]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[10:13:20]   Checking for directory '/dev/ptyxx'             [ Not found ]
[10:13:20] Ambient (ark) Rootkit                             [ Not found ]
[10:13:20]
[10:13:20] Checking for Balaur Rootkit...
[10:13:20]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[10:13:20]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[10:13:20]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[10:13:20]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[10:13:20] Balaur Rootkit                                    [ Not found ]
[10:13:21]
[10:13:21] Checking for BeastKit Rootkit...
[10:13:21]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[10:13:21]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[10:13:21]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[10:13:21]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[10:13:22] BeastKit Rootkit                                  [ Not found ]
[10:13:22]
[10:13:22] Checking for beX2 Rootkit...
[10:13:22]   Checking for directory '/usr/include/bex'       [ Not found ]
[10:13:22] beX2 Rootkit                                      [ Not found ]
[10:13:22]
[10:13:22] Checking for BOBKit Rootkit...
[10:13:22]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[10:13:22]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../find'           [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../du'             [ Not found ]
[10:13:23]   Checking for file '/usr/lib/.../top'            [ Not found ]
[10:13:23]   Checking for directory '/usr/lib/...'           [ Not found ]
[10:13:23]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[10:13:23]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[10:13:24]   Checking for directory '/tmp/.bkp'              [ Not found ]
[10:13:24] BOBKit Rootkit                                    [ Not found ]
[10:13:24]
[10:13:24] Checking for CiNIK Worm (Slapper.B variant)...
[10:13:24]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:13:24]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[10:13:24] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[10:13:24]
[10:13:24] Checking for Danny-Boy's Abuse Kit...
[10:13:24]   Checking for file '/dev/mdev'                   [ Not found ]
[10:13:24]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[10:13:24] Danny-Boy's Abuse Kit                             [ Not found ]
[10:13:24]
[10:13:24] Checking for Devil RootKit...
[10:13:25]   Checking for file '/var/lib/games/.src'         [ Not found ]
[10:13:25]   Checking for file '/dev/dsx'                    [ Not found ]
[10:13:25]   Checking for file '/dev/caca'                   [ Not found ]
[10:13:25] Devil RootKit                                     [ Not found ]
[10:13:25]
[10:13:25] Checking for Dica-Kit Rootkit...
[10:13:25]   Checking for file '/lib/.sso'                   [ Not found ]
[10:13:25]   Checking for file '/lib/.so'                    [ Not found ]
[10:13:25]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[10:13:25]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[10:13:25]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[10:13:25]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[10:13:26]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[10:13:26]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[10:13:26]   Checking for file '/var/run/...dica/va'         [ Not found ]
[10:13:26]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[10:13:26]   Checking for file '/usr/bin/.etc'               [ Not found ]
[10:13:26]   Checking for directory '/var/run/...dica'       [ Not found ]
[10:13:26]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[10:13:26]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[10:13:26] Dica-Kit Rootkit                                  [ Not found ]
[10:13:26]
[10:13:26] Checking for Dreams Rootkit...
[10:13:26]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:13:27]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:13:27]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:13:27]   Checking for file '/usr/bin/sense'              [ Not found ]
[10:13:27]   Checking for file '/usr/bin/sl2'                [ Not found ]
[10:13:27]   Checking for file '/usr/bin/logclear'           [ Not found ]
[10:13:27]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[10:13:27]   Checking for file '/usr/bin/snfs'               [ Not found ]
[10:13:27]   Checking for file '/usr/lib/libsss'             [ Not found ]
[10:13:27]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[10:13:27] Dreams Rootkit                                    [ Not found ]
[10:13:27]
[10:13:27] Checking for Duarawkz Rootkit...
[10:13:27]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[10:13:28]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[10:13:28] Duarawkz Rootkit                                  [ Not found ]
[10:13:28]
[10:13:28] Checking for Enye LKM...
[10:13:28]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[10:13:28] Enye LKM                                          [ Not found ]
[10:13:28]
[10:13:28] Checking for Flea Linux Rootkit...
[10:13:28]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:13:28]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[10:13:28]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[10:13:28]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[10:13:28]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:13:28]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[10:13:29]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[10:13:29]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[10:13:29]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[10:13:29]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:13:29]   Checking for directory '/dev/..0'               [ Not found ]
[10:13:29]   Checking for directory '/dev/..0/backup'        [ Not found ]
[10:13:29] Flea Linux Rootkit                                [ Not found ]
[10:13:29]
[10:13:29] Checking for FreeBSD Rootkit...
[10:13:29]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[10:13:29]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[10:13:29]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[10:13:30]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[10:13:30]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[10:13:30]   Checking for file '/bin/sysback'                [ Not found ]
[10:13:30]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[10:13:30]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[10:13:30]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[10:13:30] FreeBSD Rootkit                                   [ Not found ]
[10:13:30]
[10:13:30] Checking for ****`it Rootkit...
[10:13:30]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[10:13:30]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[10:13:30]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[10:13:31]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[10:13:31]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[10:13:31]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[10:13:31]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[10:13:31]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[10:13:31] ****`it Rootkit                                   [ Not found ]
[10:13:31]
[10:13:31] Checking for GasKit Rootkit...
[10:13:31]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[10:13:31]   Checking for directory '/dev/dev'               [ Not found ]
[10:13:31]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[10:13:31]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[10:13:32] GasKit Rootkit                                    [ Not found ]
[10:13:32]
[10:13:32] Checking for Heroin LKM...
[10:13:32]   Checking for kernel symbol 'heroin'             [ Not found ]
[10:13:32] Heroin LKM                                        [ Not found ]
[10:13:32]
[10:13:32] Checking for HjC Kit...
[10:13:32]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[10:13:32] HjC Kit                                           [ Not found ]
[10:13:32]
[10:13:32] Checking for ignoKit Rootkit...
[10:13:32]   Checking for file '/lib/defs/p'                 [ Not found ]
[10:13:32]   Checking for file '/lib/defs/q'                 [ Not found ]
[10:13:32]   Checking for file '/lib/defs/r'                 [ Not found ]
[10:13:32]   Checking for file '/lib/defs/s'                 [ Not found ]
[10:13:32]   Checking for file '/lib/defs/t'                 [ Not found ]
[10:13:33]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[10:13:33]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[10:13:33]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[10:13:33]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[10:13:33]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[10:13:33]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[10:13:33]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[10:13:33]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[10:13:33]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[10:13:33] ignoKit Rootkit                                   [ Not found ]
[10:13:33]
[10:13:33] Checking for ImperalsS-FBRK Rootkit...
[10:13:34]   Checking for directory '/dev/fd/.88'            [ Not found ]
[10:13:34]   Checking for directory '/dev/fd/.99'            [ Not found ]
[10:13:34] ImperalsS-FBRK Rootkit                            [ Not found ]
[10:13:34]
[10:13:34] Checking for Irix Rootkit...
[10:13:34]   Checking for directory '/dev/pts/01'            [ Not found ]
[10:13:34]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[10:13:34]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[10:13:34]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[10:13:34] Irix Rootkit                                      [ Not found ]
[10:13:34]
[10:13:34] Checking for Kitko Rootkit...
[10:13:34]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[10:13:34] Kitko Rootkit                                     [ Not found ]
[10:13:35]
[10:13:35] Checking for Knark Rootkit...
[10:13:35]   Checking for file '/proc/knark/pids'            [ Not found ]
[10:13:35]   Checking for directory '/proc/knark'            [ Not found ]
[10:13:35] Knark Rootkit                                     [ Not found ]
[10:13:35]
[10:13:35] Checking for Li0n Worm...
[10:13:35]   Checking for file '/bin/in.telnetd'             [ Not found ]
[10:13:35]   Checking for file '/bin/mjy'                    [ Not found ]
[10:13:35]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[10:13:35]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[10:13:35]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[10:13:35]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[10:13:36]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[10:13:37]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[10:13:37] Li0n Worm                                         [ Not found ]
[10:13:38]
[10:13:38] Checking for Lockit / LJK2 Rootkit...
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[10:13:38]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[10:13:39]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[10:13:40]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[10:13:41]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[10:13:41]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[10:13:42] Lockit / LJK2 Rootkit                             [ Not found ]
[10:13:42]
[10:13:42] Checking for Mood-NT Rootkit...
[10:13:42]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[10:13:42]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[10:13:42]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[10:13:42]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[10:13:42]   Checking for directory '/_cthulhu'              [ Not found ]
[10:13:42] Mood-NT Rootkit                                   [ Not found ]
[10:13:42]
[10:13:42] Checking for MRK Rootkit...
[10:13:42]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[10:13:43]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[10:13:43]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[10:13:43]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[10:13:43]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[10:13:43]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[10:13:43] MRK Rootkit                                       [ Not found ]
[10:13:43]
[10:13:43] Checking for Ni0 Rootkit...
[10:13:43]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[10:13:44]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[10:13:44]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[10:13:44]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[10:13:44]   Checking for directory '/tmp/waza'              [ Not found ]
[10:13:44]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:13:44]   Checking for directory '/usr/sbin/es'           [ Not found ]
[10:13:44] Ni0 Rootkit                                       [ Not found ]
[10:13:44]
[10:13:44] Checking for Ohhara Rootkit...
[10:13:45]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[10:13:45]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[10:13:45] Ohhara Rootkit                                    [ Not found ]
[10:13:45]
[10:13:45] Checking for Optic Kit (Tux) Worm...
[10:13:46]   Checking for directory '/dev/tux'               [ Not found ]
[10:13:46]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[10:13:46]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[10:13:46]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[10:13:46] Optic Kit (Tux) Worm                              [ Not found ]
[10:13:46]
[10:13:46] Checking for Oz Rootkit...
[10:13:46]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[10:13:46]   Checking for directory '/dev/.oz'               [ Not found ]
[10:13:46] Oz Rootkit                                        [ Not found ]
[10:13:47]
[10:13:47] Checking for Phalanx Rootkit...
[10:13:47]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[10:13:47]   Checking for file '/etc/host.ph1'               [ Not found ]
[10:13:47]   Checking for file '/bin/host.ph1'               [ Not found ]
[10:13:47]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[10:13:47]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[10:13:47] Phalanx Rootkit                                   [ Not found ]
[10:13:47]
[10:13:47] Checking for Phalanx Rootkit (strings)...
[10:13:48]   Checking for string 'phalanx'                   [ Not found ]
[10:13:48] Phalanx Rootkit (strings)                         [ Not found ]
[10:13:48]
[10:13:48] Checking for Portacelo Rootkit...
[10:13:48]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[10:13:48]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[10:13:48]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[10:13:48]   Checking for file '/var/lib/.../.p'             [ Not found ]
[10:13:48]   Checking for file '/var/lib/.../getty'          [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../show'           [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[10:13:49]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[10:13:49]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[10:13:50] Portacelo Rootkit                                 [ Not found ]
[10:13:50]
[10:13:50] Checking for R3dstorm Toolkit...
[10:13:50]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[10:13:50]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[10:13:50]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[10:13:50]   Checking for file '/bin/.../see_all'            [ Not found ]
[10:13:50]   Checking for directory '/var/log/tk02'          [ Not found ]
[10:13:50]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[10:13:51]   Checking for directory '/bin/...'               [ Not found ]
[10:13:51] R3dstorm Toolkit                                  [ Not found ]
[10:13:51]
[10:13:51] Checking for RH-Sharpe's Rootkit...
[10:13:51]   Checking for file '/bin/lps'                    [ Not found ]
[10:13:51]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[10:13:51]   Checking for file '/usr/bin/ltop'               [ Not found ]
[10:13:51]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[10:13:51]   Checking for file '/usr/bin/ldu'                [ Not found ]
[10:13:52]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[10:13:52]   Checking for file '/usr/bin/wp'                 [ Not found ]
[10:13:52]   Checking for file '/usr/bin/shad'               [ Not found ]
[10:13:52]   Checking for file '/usr/bin/vadim'              [ Not found ]
[10:13:52]   Checking for file '/usr/bin/slice'              [ Not found ]
[10:13:52]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[10:13:52]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[10:13:53] RH-Sharpe's Rootkit                               [ Not found ]
[10:13:53]
[10:13:53] Checking for RSHA's Rootkit...
[10:13:53]   Checking for file '/bin/kr4p'                   [ Not found ]
[10:13:53]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[10:13:53]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[10:13:53]   Checking for file '/usr/bin/slice2'             [ Not found ]
[10:13:53]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[10:13:53]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[10:13:54]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[10:13:54]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[10:13:54] RSHA's Rootkit                                    [ Not found ]
[10:13:54]
[10:13:54] Checking for Scalper Worm...
[10:13:54]   Checking for file '/tmp/.a'                     [ Not found ]
[10:13:54]   Checking for file '/tmp/.uua'                   [ Not found ]
[10:13:55] Scalper Worm                                      [ Not found ]
[10:13:55]
[10:13:55] Checking for Sebek LKM...
[10:13:55]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[10:13:55] Sebek LKM                                         [ Not found ]
[10:13:55]
[10:13:55] Checking for Shutdown Rootkit...
[10:13:55]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[10:13:55]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[10:13:55]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[10:13:56]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[10:13:56]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[10:13:56]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[10:13:56]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[10:13:56]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[10:13:56] Shutdown Rootkit                                  [ Not found ]
[10:13:56]
[10:13:56] Checking for SHV4 Rootkit...
[10:13:57]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:13:57]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:13:57]   Checking for file '/lib/lidps1.so'              [ Not found ]
[10:13:57]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[10:13:57]   Checking for directory '/lib/security/.config'  [ Not found ]
[10:13:58]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[10:13:58] SHV4 Rootkit                                      [ Not found ]
[10:13:58]
[10:13:58] Checking for SHV5 Rootkit...
[10:13:58]   Checking for file '/etc/sh.conf'                [ Not found ]
[10:13:58]   Checking for file '/dev/srd0'                   [ Not found ]
[10:13:58]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[10:13:58] SHV5 Rootkit                                      [ Not found ]
[10:13:59]
[10:13:59] Checking for Sin Rootkit...
[10:13:59]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[10:13:59]   Checking for file '/dev/ttyoa'                  [ Not found ]
[10:13:59]   Checking for file '/dev/ttyof'                  [ Not found ]
[10:13:59]   Checking for file '/dev/ttyop'                  [ Not found ]
[10:13:59]   Checking for file '/dev/ttyos'                  [ Not found ]
[10:13:59]   Checking for file '/usr/lib/.lib'               [ Not found ]
[10:13:59]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[10:14:00]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[10:14:00]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[10:14:00]   Checking for file '/usr/man/man1/...'           [ Not found ]
[10:14:00]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[10:14:00]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[10:14:01]   Checking for directory '/usr/lib/sn'            [ Not found ]
[10:14:01]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[10:14:01]   Checking for directory '/dev/.haos'             [ Not found ]
[10:14:01] Sin Rootkit                                       [ Not found ]
[10:14:02]
[10:14:02] Checking for Slapper Worm...
[10:14:02]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[10:14:02]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[10:14:02]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[10:14:02]   Checking for file '/tmp/httpd'                  [ Not found ]
[10:14:02]   Checking for file '/tmp/.unlock'                [ Not found ]
[10:14:02]   Checking for file '/tmp/update'                 [ Not found ]
[10:14:03]   Checking for file '/tmp/.cinik'                 [ Not found ]
[10:14:03]   Checking for file '/tmp/.b'                     [ Not found ]
[10:14:03] Slapper Worm                                      [ Not found ]
[10:14:03]
[10:14:03] Checking for Sneakin Rootkit...
[10:14:03]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[10:14:03] Sneakin Rootkit                                   [ Not found ]
[10:14:03]
[10:14:03] Checking for Suckit Rootkit...
[10:14:03]   Checking for file '/sbin/initsk12'              [ Not found ]
[10:14:03]   Checking for file '/sbin/initxrk'               [ Not found ]
[10:14:03]   Checking for file '/usr/bin/null'               [ Not found ]
[10:14:03]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[10:14:04]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[10:14:04]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[10:14:04]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[10:14:04]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[10:14:04]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[10:14:05]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[10:14:05]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[10:14:05]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[10:14:05]   Checking for directory '/etc/.MG'               [ Not found ]
[10:14:06]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[10:14:06]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[10:14:06] Suckit Rootkit                                    [ Not found ]
[10:14:06]
[10:14:06] Checking for SunOS Rootkit...
[10:14:06]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[10:14:06]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[10:14:06]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[10:14:06]   Checking for file '/bin/xlogin'                 [ Not found ]
[10:14:06]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[10:14:06]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[10:14:06]   Checking for file '/sbin/login'                 [ Not found ]
[10:14:07]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[10:14:07]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[10:14:07]   Checking for file '/dev/kmod'                   [ Not found ]
[10:14:07]   Checking for file '/dev/dos'                    [ Not found ]
[10:14:07] SunOS Rootkit                                     [ Not found ]
[10:14:07]
[10:14:07] Checking for SunOS / NSDAP Rootkit...
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[10:14:07]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[10:14:08]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[10:14:08]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[10:14:08]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[10:14:08]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[10:14:08]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[10:14:08]   Checking for file '/usr/lib/lpset'              [ Not found ]
[10:14:08]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[10:14:08] SunOS / NSDAP Rootkit                             [ Not found ]
[10:14:08]
[10:14:08] Checking for Superkit Rootkit...
[10:14:08]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[10:14:09] Superkit Rootkit                                  [ Not found ]
[10:14:09]
[10:14:09] Checking for TBD (Telnet BackDoor)...
[10:14:09]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[10:14:09] TBD (Telnet BackDoor)                             [ Not found ]
[10:14:09]
[10:14:09] Checking for TeLeKiT Rootkit...
[10:14:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[10:14:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[10:14:09]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[10:14:09]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[10:14:09]   Checking for file '/dev/ptyr'                   [ Not found ]
[10:14:09]   Checking for file '/dev/ptyp'                   [ Not found ]
[10:14:09]   Checking for file '/dev/ptyq'                   [ Not found ]
[10:14:09]   Checking for file '/dev/hda06'                  [ Not found ]
[10:14:10]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[10:14:10]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[10:14:10]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[10:14:10]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[10:14:10] TeLeKiT Rootkit                                   [ Not found ]
[10:14:10]
[10:14:10] Checking for T0rn Rootkit...
[10:14:10]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[10:14:10]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[10:14:10]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[10:14:10]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[10:14:10]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[10:14:10]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[10:14:11]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[10:14:12]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[10:14:12]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[10:14:12]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[10:14:12]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[10:14:12]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[10:14:12]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[10:14:12]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[10:14:12]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[10:14:12]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[10:14:12]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[10:14:12]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[10:14:12]   Checking for directory '/dev/.lib'              [ Not found ]
[10:14:13]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[10:14:13]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[10:14:13]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[10:14:13]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[10:14:13]   Checking for directory '/usr/src/.****'         [ Not found ]
[10:14:13]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[10:14:13]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[10:14:13]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[10:14:13]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[10:14:13] T0rn Rootkit                                      [ Not found ]
[10:14:13]
[10:14:13] Checking for Trojanit Kit...
[10:14:13]   Checking for file '/bin/.ls'                    [ Not found ]
[10:14:14]   Checking for file '/bin/.ps'                    [ Not found ]
[10:14:14]   Checking for file '/bin/.netstat'               [ Not found ]
[10:14:14]   Checking for file '/usr/bin/.nop'               [ Not found ]
[10:14:14]   Checking for file '/usr/bin/.who'               [ Not found ]
[10:14:14] Trojanit Kit                                      [ Not found ]
[10:14:14]
[10:14:14] Checking for Tuxtendo Rootkit...
[10:14:14]   Checking for file '/dev/tux/.addr'              [ Not found ]
[10:14:14]   Checking for file '/dev/tux/.cron'              [ Not found ]
[10:14:14]   Checking for file '/dev/tux/.file'              [ Not found ]
[10:14:14]   Checking for file '/dev/tux/.log'               [ Not found ]
[10:14:14]   Checking for file '/dev/tux/.proc'              [ Not found ]
[10:14:14]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[10:14:15]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[10:14:16]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[10:14:16]   Checking for directory '/dev/tux'               [ Not found ]
[10:14:16]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[10:14:16]   Checking for directory '/dev/tux/backup'        [ Not found ]
[10:14:16] Tuxtendo Rootkit                                  [ Not found ]
[10:14:16]
[10:14:16] Checking for URK Rootkit...
[10:14:16]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[10:14:16]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[10:14:16]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[10:14:16]   Checking for file '/tmp/conf.inf'               [ Not found ]
[10:14:16]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[10:14:16] URK Rootkit                                       [ Not found ]
[10:14:17]
[10:14:17] Checking for VcKit Rootkit...
[10:14:17]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[10:14:17]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[10:14:17] VcKit Rootkit                                     [ Not found ]
[10:14:17]
[10:14:17] Checking for Volc Rootkit...
[10:14:17]   Checking for directory '/var/spool/.recent'     [ Not found ]
[10:14:17]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[10:14:17]   Checking for directory '/usr/lib/volc'          [ Not found ]
[10:14:17]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[10:14:17] Volc Rootkit                                      [ Not found ]
[10:14:17]
[10:14:17] Checking for X-Org SunOS Rootkit...
[10:14:17]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[10:14:18]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[10:14:18]   Checking for file '/usr/bin/srload'             [ Not found ]
[10:14:18]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[10:14:18]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[10:14:18]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[10:14:18]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[10:14:18]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[10:14:18]   Checking for directory '/usr/share/man...'      [ Not found ]
[10:14:18] X-Org SunOS Rootkit                               [ Not found ]
[10:14:18]
[10:14:18] Checking for zaRwT.KiT Rootkit...
[10:14:18]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[10:14:18]   Checking for file '/dev/ttyf'                   [ Not found ]
[10:14:18]   Checking for file '/dev/ttyp'                   [ Not found ]
[10:14:19]   Checking for file '/dev/ttyn'                   [ Not found ]
[10:14:19]   Checking for file '/rk/tulz'                    [ Not found ]
[10:14:19]   Checking for directory '/rk'                    [ Not found ]
[10:14:19]   Checking for directory '/dev/rd/s'              [ Not found ]
[10:14:19] zaRwT.KiT Rootkit                                 [ Not found ]
[10:14:19]
[10:14:19] Performing additional rootkit checks
[10:14:19] Info: Starting test name 'additional_rkts'
[10:14:19]
[10:14:19]   Performing Suckit Rookit additional checks
[10:14:19]     Checking /sbin/init link count                [ OK ]
[10:14:19]     Checking for hidden file extensions           [ None found ]
[10:14:19]     Running skdet command                         [ Skipped ]
[10:14:19] Info: Unable to find the 'skdet' command
[10:14:20]   Suckit Rookit additional checks                 [ OK ]
[10:14:20]
[10:14:20]   Performing check of possible rootkit files and directories
[10:14:20] Info: Starting test name 'possible_rkt_files'
[10:14:20]     Checking for file '/dev/sdr0'                 [ Not found ]
[10:14:20]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[10:14:20]     Checking for file '/tmp/.bash_history'        [ Not found ]
[10:14:20]     Checking for file '/usr/info/.clib'           [ Not found ]
[10:14:20]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[10:14:20]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[10:14:20]     Checking for file '/sbin/create'              [ Not found ]
[10:14:21]     Checking for file '/dev/ttypz'                [ Not found ]
[10:14:21]     Checking for directory '/usr/bin/take'        [ Not found ]
[10:14:21]     Checking for directory '/usr/src/.lib'        [ Not found ]
[10:14:21]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[10:14:21]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[10:14:21]     Checking for directory '/usr/sbin/...'        [ Not found ]
[10:14:21]     Checking for directory '/usr/share/.gun'      [ Not found ]
[10:14:21]   Checking for possible rootkit files and directories [ None found ]
[10:14:21]
[10:14:21]   Performing check for possible rootkit strings
[10:14:21] Info: Starting test name 'possible_rkt_strings'
[10:14:21] Info: Found local startup file: /etc/rc.local
[10:14:21] Info: Found local startup file: /etc/inittab
[10:14:22]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:14:22]     Checking for string '****'                    [ Not found ]
[10:14:22]     Checking for string 'backdoor'                [ Not found ]
[10:14:22]     Checking for string 'vt200'                   [ Not found ]
[10:14:22]     Checking for string '/usr/bin/xstat'          [ Not found ]
[10:14:22]     Checking for string '/bin/envpc'              [ Not found ]
[10:14:22]     Checking for string 'L4m3r0x'                 [ Not found ]
[10:14:22]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:14:23]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[10:14:23]     Checking for string '/dev/sgk'                [ Not found ]
[10:14:23]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:14:23]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:14:23]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[10:14:23]     Checking for string '/lib/.sso'               [ Not found ]
[10:14:23]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:14:24]     Checking for string '/dev/caca'               [ Not found ]
[10:14:24]     Checking for string '/dev/ttyoa'              [ Not found ]
[10:14:24]     Checking for string 'syg'                     [ Not found ]
[10:14:24]     Checking for string '/dev/pts/01'             [ Not found ]
[10:14:24]     Checking for string 'tw33dl3'                 [ Not found ]
[10:14:24]     Checking for string 'psniff'                  [ Not found ]
[10:14:24]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[10:14:25]     Checking for string 'promiscuous'             [ Not found ]
[10:14:25]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:14:25]     Checking for string '/dev/xdta'               [ Not found ]
[10:14:25]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[10:14:25]     Checking for string 'in.inetd'                [ Not found ]
[10:14:25]     Checking for string '#<HIDE_.*>'              [ Not found ]
[10:14:25]     Checking for string 'bin/xchk'                [ Not found ]
[10:14:26]     Checking for string 'bin/xsf'                 [ Not found ]
[10:14:26]   Checking for possible rootkit strings           [ None found ]
[10:14:26]
[10:14:26] Performing malware checks
[10:14:26] Info: Starting test name 'malware'
[10:14:26]
[10:14:26] Info: Test 'deleted_files' disabled at users request.
[10:14:26] Info: Starting test name 'running_procs'
[10:14:26]   Checking running processes for suspicious files [ None found ]
[10:14:26]
[10:14:26] Info: Test 'hidden_procs' disabled at users request.
[10:14:27]
[10:14:27] Info: Test 'suspscan' disabled at users request.
[10:14:27]
[10:14:27]   Performing check for login backdoors
[10:14:27] Info: Starting test name 'other_malware'
[10:14:27]     Checking for '/bin/.login'                    [ Not found ]
[10:14:27]     Checking for '/sbin/.login'                   [ Not found ]
[10:14:27]   Checking for login backdoors                    [ None found ]
[10:14:27]
[10:14:27]   Performing check for suspicious directories
[10:14:27]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[10:14:27]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[10:14:27]   Checking for suspicious directories             [ None found ]
[10:14:27]
[10:14:27]   Checking for software intrusions                [ Skipped ]
[10:14:27] Info: Check skipped - tripwire not installed
[10:14:27]
[10:14:27]   Performing check for sniffer log files
[10:14:27]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[10:14:27]   Checking for sniffer log files                  [ None found ]
[10:14:28]
[10:14:28] Performing trojan specific checks
[10:14:28] Info: Starting test name 'trojans'
[10:14:28] Info: Using inetd configuration file '/etc/inetd.conf'
[10:14:28]   Checking for enabled inetd services             [ Warning ]
[10:14:28] Warning: Found enabled inetd service: ident
[10:14:28]
[10:14:28]   Performing check for enabled xinetd services
[10:14:28]   Checking for enabled xinetd services            [ Skipped ]
[10:14:28] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[10:14:28] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[10:14:28]
[10:14:28] Performing Linux specific checks
[10:14:28] Info: Starting test name 'os_specific'
[10:14:28]   Checking kernel module commands                 [ OK ]
[10:14:28] Info: Using modules pathname of '/lib/modules/2.6.24-1-686'
[10:14:31]   Checking kernel module names                    [ OK ]
[10:14:31]
[10:14:31] Checking the network...
[10:14:31] Info: Starting test name 'network'
[10:14:31] Info: Starting test name 'ports'
[10:14:31]
[10:14:31] Performing check for backdoor ports
[10:14:31]   Checking for UDP port 2001                      [ Not found ]
[10:14:31]   Checking for TCP port 2006                      [ Not found ]
[10:14:31]   Checking for TCP port 2128                      [ Not found ]
[10:14:32]   Checking for TCP port 14856                     [ Not found ]
[10:14:32]   Checking for TCP port 47107                     [ Not found ]
[10:14:32]   Checking for TCP port 60922                     [ Not found ]
[10:14:32]
[10:14:32] Performing checks on the network interfaces
[10:14:32] Info: Starting test name 'promisc'
[10:14:32]   Checking for promiscuous interfaces             [ None found ]
[10:14:32]
[10:14:32] Info: Test 'packet_cap_apps' disabled at users request.
[10:14:33]
[10:14:33] Checking the local host...
[10:14:33] Info: Starting test name 'local_host'
[10:14:33]
[10:14:33] Performing system boot checks
[10:14:33] Info: Starting test name 'startup_files'
[10:14:33]   Checking for local host name                    [ Found ]
[10:14:33] Info: Starting test name 'startup_malware'
[10:14:33] Info: Found local startup file: /etc/rc.local
[10:14:33] Info: Found local startup file: /etc/inittab
[10:14:33]   Checking for local startup files                [ Found ]
[10:14:33]   Checking local startup files for malware        [ None found ]
[10:14:33] Info: Found system startup directory: /etc/init.d
[10:14:36]   Checking system startup files for malware       [ None found ]
[10:14:36]
[10:14:36] Performing group and account checks
[10:14:36] Info: Starting test name 'group_accounts'
[10:14:36]   Checking for passwd file                        [ Found ]
[10:14:36] Info: Found password file: /etc/passwd
[10:14:36]   Checking for root equivalent (UID 0) accounts   [ None found ]
[10:14:36] Info: Found shadow file: /etc/shadow
[10:14:36]   Checking for passwordless accounts              [ None found ]
[10:14:36] Info: Starting test name 'passwd_changes'
[10:14:36]   Checking for passwd file changes                [ None found ]
[10:14:36] Info: Starting test name 'group_changes'
[10:14:37]   Checking for group file changes                 [ None found ]
[10:14:37]   Checking root account shell history files       [ OK ]
[10:14:37]
[10:14:37] Performing system configuration file checks
[10:14:37] Info: Starting test name 'system_configs'
[10:14:37]   Checking for SSH configuration file             [ Not found ]
[10:14:37]   Checking for running syslog daemon              [ Found ]
[10:14:37]   Checking for syslog configuration file          [ Found ]
[10:14:37] Info: Found syslog configuration file: /etc/syslog.conf
[10:14:37]   Checking if syslog remote logging is allowed    [ Not allowed ]
[10:14:38]
[10:14:38] Performing filesystem checks
[10:14:38] Info: Starting test name 'filesystem'
[10:14:38] Info: SCAN_MODE_DEV set to 'THOROUGH'
[10:15:36]   Checking /dev for suspicious file types         [ None found ]
[10:15:36]   Checking for hidden files and directories       [ Warning ]
[10:15:37] Warning: Hidden directory found: /etc/.java
[10:15:37] Warning: Hidden directory found: /dev/.static
[10:15:37] Warning: Hidden directory found: /dev/.udev
[10:15:37] Warning: Hidden directory found: /dev/.initramfs
[10:15:37]
[10:15:37] Checking application versions...
[10:15:37] Info: Starting test name 'apps'
[10:15:38]   Checking version of Exim MTA                    [ OK ]
[10:15:38] Info: Application 'exim' version '4.69' found.
[10:15:38]   Checking version of GnuPG                       [ OK ]
[10:15:38] Info: Application 'gpg' version '1.4.6' found.
[10:15:38] Info: Application 'httpd' not found.
[10:15:38] Info: Application 'named' not found.
[10:15:39]   Checking version of OpenSSL                     [ OK ]
[10:15:39] Info: Application 'openssl' version '0.9.8g' found.
[10:15:39] Info: Application 'php' not found.
[10:15:39]   Checking version of Procmail MTA                [ OK ]
[10:15:39] Info: Application 'procmail' version '3.22' found.
[10:15:39] Info: Application 'proftpd' not found.
[10:15:39] Info: Application 'sshd' not found.
[10:15:39] Info: Applications checked: 4 out of 9
[10:15:39]
[10:15:39] System checks summary
[10:15:39] =====================
[10:15:39]
[10:15:39] File properties checks...
[10:15:39] Files checked: 128
[10:15:39] Suspect files: 59
[10:15:39]
[10:15:39] Rootkit checks...
[10:15:39] Rootkits checked : 109
[10:15:40] Possible rootkits: 0
[10:15:40]
[10:15:40] Applications checks...
[10:15:40] Applications checked: 4
[10:15:40] Suspect applications: 0
[10:15:40]
[10:15:40] The system checks took: 3 minutes and 29 seconds
[10:15:40]
[10:15:40] Info: End date is Sun Feb 10 10:15:40 PST 2008


---

### Post by jimmyridge on 2008-03-26
dunno if this is on topic but i just discovered some1 using my ubuntu server nefariously 

evidently i must have left my "test" users passowrd to something simple and it got brute forced thats not too smart having a username as test / admin / guest / any other common username

i noticed something was up when i saw ports 6667 and 7000 established with netstat (while no users but me were logged in)had a hell of a time finding the culprit i shoulda looked at netstats PID info fist but it slipped my mind 

netstat showed program bash connecting to irc (eggdrop) without looking at pid and stuff i freaked but later searched the test users home dir after removing the test user / killing the proccess and adding an iptables rule to drop outbound from those ports 

evidently someone got in my test users account and setup an eggdrop/bottnet script/bin here's what i found if you care to look at it it was in /home/test/.ssh/.m   [http://hst.ath.cx/~james/noob](http://hst.ath.cx/~james/noob)
pretty funny actually now that i cleaned it up :lolflag:  

now i have fail2ban running <brute force counter measure> dunno if they brute forced it or what i had givin the user/pass info out to some friends in irc

---

