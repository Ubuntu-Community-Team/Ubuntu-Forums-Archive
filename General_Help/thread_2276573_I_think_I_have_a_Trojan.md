---
title: "I think I have a Trojan"
date: 2015-05-03
forum: General Help
---

### Post by Pablo_Alvaro_Moran on 2015-05-03
i'm developing a python app in my laptop. I use WSGI server (Bottle)
when i check the log mi server is making request a chinese site !!


This is the output of chkrootkit:

```
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not found
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not found
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-1.7.0-openjdk-amd64.jinfo


Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[878], /sbin/dhclient[12064])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            chklastlog: nothing deleted
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root        12199 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected

```

And this rkhunter output:
```
[19:40:08] Running Rootkit Hunter version 1.4.0 on neganix-AO756
[19:40:08]
[19:40:08] Info: Start date is dom may  3 19:40:08 CEST 2015
[19:40:09]
[19:40:09] Checking configuration file and command-line options...
[19:40:09] Info: Detected operating system is 'Linux'
[19:40:09] Info: Found O/S name: Ubuntu 14.04.2 LTS
[19:40:09] Info: Command line is /usr/bin/rkhunter --check
[19:40:09] Info: Environment shell is /bin/bash; rkhunter is using dash
[19:40:09] Info: Using configuration file '/etc/rkhunter.conf'
[19:40:09] Info: Installation directory is '/usr'
[19:40:09] Info: Using language 'en'
[19:40:09] Info: Using '/var/lib/rkhunter/db' as the database directory
[19:40:09] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[19:40:09] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin' as the command directories
[19:40:09] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[19:40:09] Info: No mail-on-warning address configured
[19:40:09] Info: X will be automatically detected
[19:40:09] Info: Using second color set
[19:40:09] Info: Found the 'basename' command: /usr/bin/basename
[19:40:09] Info: Found the 'diff' command: /usr/bin/diff
[19:40:09] Info: Found the 'dirname' command: /usr/bin/dirname
[19:40:09] Info: Found the 'file' command: /usr/bin/file
[19:40:09] Info: Found the 'find' command: /usr/bin/find
[19:40:09] Info: Found the 'ifconfig' command: /sbin/ifconfig
[19:40:09] Info: Found the 'ip' command: /sbin/ip
[19:40:09] Info: Found the 'ldd' command: /usr/bin/ldd
[19:40:09] Info: Found the 'lsattr' command: /usr/bin/lsattr
[19:40:09] Info: Found the 'lsmod' command: /sbin/lsmod
[19:40:09] Info: Found the 'lsof' command: /usr/bin/lsof
[19:40:09] Info: Found the 'mktemp' command: /bin/mktemp
[19:40:09] Info: Found the 'netstat' command: /bin/netstat
[19:40:09] Info: Found the 'perl' command: /usr/bin/perl
[19:40:09] Info: Found the 'pgrep' command: /usr/bin/pgrep
[19:40:09] Info: Found the 'ps' command: /bin/ps
[19:40:09] Info: Found the 'pwd' command: /bin/pwd
[19:40:09] Info: Found the 'readlink' command: /bin/readlink
[19:40:09] Info: Found the 'stat' command: /usr/bin/stat
[19:40:09] Info: Found the 'strings' command: /usr/bin/strings
[19:40:09] Info: System is not using prelinking
[19:40:09] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[19:40:09] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[19:40:09] Info: Stored hash values did not use a package manager
[19:40:09] Info: The hash function field index is set to 1
[19:40:09] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[19:40:09] Info: Previous file attributes were stored
[19:40:09] Info: Enabled tests are: all
[19:40:09] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps apps
[19:40:09] Info: Found ksym file '/proc/kallsyms'
[19:40:09] Info: Using 'date' to process epoch second times.
[19:40:09]
[19:40:09] Checking if the O/S has changed since last time...
[19:40:09] Info: Nothing seems to have changed.
[19:40:09] Info: Locking is not being used
[19:40:09]
[19:40:09] Starting system checks...
[19:40:09]
[19:40:09] Info: Starting test name 'system_commands'
[19:40:09] Checking system commands...
[19:40:10]
[19:40:10] Info: Starting test name 'strings'
[19:40:10] Performing 'strings' command checks
[19:40:10]   Scanning for string /usr/sbin/ntpsx             [ OK ]
[19:40:10]   Scanning for string /usr/sbin/.../bkit-ava      [ OK ]
[19:40:10]   Scanning for string /usr/sbin/.../bkit-d        [ OK ]
[19:40:10]   Scanning for string /usr/sbin/.../bkit-shd      [ OK ]
[19:40:10]   Scanning for string /usr/sbin/.../bkit-f        [ OK ]
[19:40:10]   Scanning for string /usr/include/.../proc.h     [ OK ]
[19:40:10]   Scanning for string /usr/include/.../.bash_history [ OK ]
[19:40:10]   Scanning for string /usr/include/.../bkit-get   [ OK ]
[19:40:10]   Scanning for string /usr/include/.../bkit-dl    [ OK ]
[19:40:10]   Scanning for string /usr/include/.../bkit-screen [ OK ]
[19:40:10]   Scanning for string /usr/include/.../bkit-sleep [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-adore.o   [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../ls             [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../netstat        [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../lsof           [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../bkit-ssh/bkit-mots [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../uconf.inv      [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../psr            [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../find           [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../pstree         [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../slocate        [ OK ]
[19:40:10]   Scanning for string /usr/lib/.../du             [ OK ]
[19:40:11]   Scanning for string /usr/lib/.../top            [ OK ]
[19:40:11]   Scanning for string /usr/sbin/...               [ OK ]
[19:40:11]   Scanning for string /usr/include/...            [ OK ]
[19:40:11]   Scanning for string /usr/include/.../.tmp       [ OK ]
[19:40:11]   Scanning for string /usr/lib/...                [ OK ]
[19:40:11]   Scanning for string /usr/lib/.../.ssh           [ OK ]
[19:40:11]   Scanning for string /usr/lib/.../bkit-ssh       [ OK ]
[19:40:11]   Scanning for string /usr/lib/.bkit-             [ OK ]
[19:40:11]   Scanning for string /tmp/.bkp                   [ OK ]
[19:40:11]   Scanning for string /tmp/.cinik                 [ OK ]
[19:40:11]   Scanning for string /tmp/.font-unix/.cinik      [ OK ]
[19:40:11]   Scanning for string /lib/.sso                   [ OK ]
[19:40:11]   Scanning for string /lib/.so                    [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/clean      [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/dxr        [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/read       [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/write      [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/lf         [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/xl         [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/xdr        [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/psg        [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/secure     [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/rdx        [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/va         [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/cl.sh      [ OK ]
[19:40:11]   Scanning for string /var/run/...dica/last.log   [ OK ]
[19:40:12]   Scanning for string /usr/bin/.etc               [ OK ]
[19:40:12]   Scanning for string /etc/sshd_config            [ OK ]
[19:40:12]   Scanning for string /etc/ssh_host_key           [ OK ]
[19:40:12]   Scanning for string /etc/ssh_random_seed        [ OK ]
[19:40:12]   Scanning for string /dev/ptyp                   [ OK ]
[19:40:12]   Scanning for string /dev/ptyq                   [ OK ]
[19:40:12]   Scanning for string /dev/ptyr                   [ OK ]
[19:40:12]   Scanning for string /dev/ptys                   [ OK ]
[19:40:12]   Scanning for string /dev/ptyt                   [ OK ]
[19:40:12]   Scanning for string /dev/fd/.88/freshb-bsd      [ OK ]
[19:40:12]   Scanning for string /dev/fd/.88/fresht          [ OK ]
[19:40:12]   Scanning for string /dev/fd/.88/zxsniff         [ OK ]
[19:40:12]   Scanning for string /dev/fd/.88/zxsniff.log     [ OK ]
[19:40:12]   Scanning for string /dev/fd/.99/.ttyf00         [ OK ]
[19:40:12]   Scanning for string /dev/fd/.99/.ttyp00         [ OK ]
[19:40:12]   Scanning for string /dev/fd/.99/.ttyq00         [ OK ]
[19:40:12]   Scanning for string /dev/fd/.99/.ttys00         [ OK ]
[19:40:12]   Scanning for string /dev/fd/.99/.pwsx00         [ OK ]
[19:40:12]   Scanning for string /etc/.acid                  [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/sched_host.2   [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/random_d.2     [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/set_pid.2      [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/setrgrp.2      [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/TOHIDE         [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/cons.saver     [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/adore/ava/ava  [ OK ]
[19:40:12]   Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[19:40:13]   Scanning for string /bin/sysback                [ OK ]
[19:40:13]   Scanning for string /usr/local/bin/sysback      [ OK ]
[19:40:13]   Scanning for string /usr/lib/.tbd               [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/t0rns     [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/du        [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/ls        [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/t0rnsb    [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/ps        [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/t0rnp     [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/find      [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/ifconfig  [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/pg        [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/ssh.tgz   [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/top       [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/sz        [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/login     [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/in.fingerd [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/1i0n.sh   [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/pstree    [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/in.telnetd [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/mjy       [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/sush      [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/tfn       [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/name      [ OK ]
[19:40:13]   Scanning for string /dev/.lib/lib/lib/getip.sh  [ OK ]
[19:40:13]   Scanning for string /usr/info/.torn/sh*         [ OK ]
[19:40:13]   Scanning for string /usr/src/.puta/.1addr       [ OK ]
[19:40:14]   Scanning for string /usr/src/.puta/.1file       [ OK ]
[19:40:14]   Scanning for string /usr/src/.puta/.1proc       [ OK ]
[19:40:14]   Scanning for string /usr/src/.puta/.1logz       [ OK ]
[19:40:14]   Scanning for string /usr/info/.t0rn             [ OK ]
[19:40:14]   Scanning for string /dev/.lib                   [ OK ]
[19:40:14]   Scanning for string /dev/.lib/lib               [ OK ]
[19:40:14]   Scanning for string /dev/.lib/lib/lib           [ OK ]
[19:40:14]   Scanning for string /dev/.lib/lib/lib/dev       [ OK ]
[19:40:14]   Scanning for string /dev/.lib/lib/scan          [ OK ]
[19:40:14]   Scanning for string /usr/src/.puta              [ OK ]
[19:40:14]   Scanning for string /usr/man/man1/man1          [ OK ]
[19:40:14]   Scanning for string /usr/man/man1/man1/lib      [ OK ]
[19:40:14]   Scanning for string /usr/man/man1/man1/lib/.lib [ OK ]
[19:40:14]   Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[19:40:14]
[19:40:14] Info: Starting test name 'shared_libs'
[19:40:14] Performing 'shared libraries' checks
[19:40:14]   Checking for preloading variables               [ None found ]
[19:40:14]   Checking for preloaded libraries                [ None found ]
[19:40:14]
[19:40:14] Info: Starting test name 'shared_libs_path'
[19:40:14]   Checking LD_LIBRARY_PATH variable               [ Not found ]
[19:40:14]
[19:40:14] Info: Starting test name 'properties'
[19:40:14] Performing file properties checks
[19:40:14]   Checking for prerequisites                      [ OK ]
[19:40:17]   /usr/sbin/adduser                               [ OK ]
[19:40:17] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[19:40:18]   /usr/sbin/chroot                                [ OK ]
[19:40:18]   /usr/sbin/cron                                  [ OK ]
[19:40:18]   /usr/sbin/groupadd                              [ OK ]
[19:40:18]   /usr/sbin/groupdel                              [ OK ]
[19:40:18]   /usr/sbin/groupmod                              [ OK ]
[19:40:18]   /usr/sbin/grpck                                 [ OK ]
[19:40:19]   /usr/sbin/nologin                               [ OK ]
[19:40:19]   /usr/sbin/pwck                                  [ OK ]
[19:40:19]   /usr/sbin/rsyslogd                              [ OK ]
[19:40:20]   /usr/sbin/tcpd                                  [ OK ]
[19:40:20]   /usr/sbin/useradd                               [ OK ]
[19:40:20]   /usr/sbin/userdel                               [ OK ]
[19:40:20]   /usr/sbin/usermod                               [ OK ]
[19:40:20]   /usr/sbin/vipw                                  [ OK ]
[19:40:20]   /usr/bin/awk                                    [ OK ]
[19:40:20]   /usr/bin/basename                               [ OK ]
[19:40:21]   /usr/bin/chattr                                 [ OK ]
[19:40:21]   /usr/bin/curl                                   [ OK ]
[19:40:21]   /usr/bin/cut                                    [ OK ]
[19:40:21]   /usr/bin/diff                                   [ OK ]
[19:40:21]   /usr/bin/dirname                                [ OK ]
[19:40:21]   /usr/bin/dpkg                                   [ OK ]
[19:40:21]   /usr/bin/dpkg-query                             [ OK ]
[19:40:21]   /usr/bin/du                                     [ OK ]
[19:40:22]   /usr/bin/env                                    [ OK ]
[19:40:22]   /usr/bin/file                                   [ OK ]
[19:40:22]   /usr/bin/find                                   [ OK ]
[19:40:22]   /usr/bin/GET                                    [ OK ]
[19:40:22]   /usr/bin/groups                                 [ OK ]
[19:40:22] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[19:40:22]   /usr/bin/head                                   [ OK ]
[19:40:22]   /usr/bin/id                                     [ OK ]
[19:40:22]   /usr/bin/killall                                [ OK ]
[19:40:23]   /usr/bin/last                                   [ OK ]
[19:40:23]   /usr/bin/lastlog                                [ OK ]
[19:40:23]   /usr/bin/ldd                                    [ OK ]
[19:40:23] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[19:40:23]   /usr/bin/less                                   [ OK ]
[19:40:23]   /usr/bin/locate                                 [ OK ]
[19:40:23]   /usr/bin/logger                                 [ OK ]
[19:40:23]   /usr/bin/lsattr                                 [ OK ]
[19:40:23]   /usr/bin/lsof                                   [ OK ]
[19:40:24]   /usr/bin/md5sum                                 [ OK ]
[19:40:24]   /usr/bin/mlocate                                [ OK ]
[19:40:24]   /usr/bin/newgrp                                 [ OK ]
[19:40:24]   /usr/bin/passwd                                 [ OK ]
[19:40:24]   /usr/bin/perl                                   [ OK ]
[19:40:24]   /usr/bin/pgrep                                  [ OK ]
[19:40:24]   /usr/bin/pkill                                  [ OK ]
[19:40:24]   /usr/bin/pstree                                 [ OK ]
[19:40:25]   /usr/bin/rkhunter                               [ OK ]
[19:40:25]   /usr/bin/runcon                                 [ OK ]
[19:40:25]   /usr/bin/sha1sum                                [ OK ]
[19:40:25]   /usr/bin/sha224sum                              [ OK ]
[19:40:25]   /usr/bin/sha256sum                              [ OK ]
[19:40:25]   /usr/bin/sha384sum                              [ OK ]
[19:40:25]   /usr/bin/sha512sum                              [ OK ]
[19:40:25]   /usr/bin/size                                   [ OK ]
[19:40:26]   /usr/bin/sort                                   [ OK ]
[19:40:26]   /usr/bin/stat                                   [ OK ]
[19:40:26]   /usr/bin/strace                                 [ OK ]
[19:40:26]   /usr/bin/strings                                [ OK ]
[19:40:26]   /usr/bin/sudo                                   [ OK ]
[19:40:26]   /usr/bin/tail                                   [ OK ]
[19:40:26]   /usr/bin/test                                   [ OK ]
[19:40:26]   /usr/bin/top                                    [ OK ]
[19:40:27]   /usr/bin/touch                                  [ OK ]
[19:40:27]   /usr/bin/tr                                     [ OK ]
[19:40:27]   /usr/bin/uniq                                   [ OK ]
[19:40:27]   /usr/bin/users                                  [ OK ]
[19:40:27]   /usr/bin/vmstat                                 [ OK ]
[19:40:27]   /usr/bin/w                                      [ OK ]
[19:40:27]   /usr/bin/watch                                  [ OK ]
[19:40:27]   /usr/bin/wc                                     [ OK ]
[19:40:27]   /usr/bin/wget                                   [ OK ]
[19:40:28]   /usr/bin/whatis                                 [ OK ]
[19:40:28]   /usr/bin/whereis                                [ OK ]
[19:40:28]   /usr/bin/which                                  [ OK ]
[19:40:28]   /usr/bin/who                                    [ OK ]
[19:40:28]   /usr/bin/whoami                                 [ OK ]
[19:40:28]   /usr/bin/unhide.rb                              [ Warning ]
[19:40:28] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[19:40:28]   /usr/bin/gawk                                   [ OK ]
[19:40:28]   /usr/bin/lwp-request                            [ OK ]
[19:40:28] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[19:40:29]   /usr/bin/w.procps                               [ OK ]
[19:40:29]   /sbin/depmod                                    [ OK ]
[19:40:29]   /sbin/fsck                                      [ OK ]
[19:40:29]   /sbin/ifconfig                                  [ OK ]
[19:40:29]   /sbin/ifdown                                    [ OK ]
[19:40:29]   /sbin/ifup                                      [ OK ]
[19:40:30]   /sbin/init                                      [ OK ]
[19:40:30]   /sbin/insmod                                    [ OK ]
[19:40:30]   /sbin/ip                                        [ OK ]
[19:40:30]   /sbin/lsmod                                     [ OK ]
[19:40:30]   /sbin/modinfo                                   [ OK ]
[19:40:30]   /sbin/modprobe                                  [ OK ]
[19:40:31]   /sbin/rmmod                                     [ OK ]
[19:40:31]   /sbin/route                                     [ OK ]
[19:40:31]   /sbin/runlevel                                  [ OK ]
[19:40:31]   /sbin/sulogin                                   [ OK ]
[19:40:31]   /sbin/sysctl                                    [ OK ]
[19:40:32]   /bin/bash                                       [ OK ]
[19:40:32]   /bin/cat                                        [ OK ]
[19:40:32]   /bin/chmod                                      [ OK ]
[19:40:32]   /bin/chown                                      [ OK ]
[19:40:32]   /bin/cp                                         [ OK ]
[19:40:32]   /bin/date                                       [ OK ]
[19:40:32]   /bin/df                                         [ OK ]
[19:40:33]   /bin/dmesg                                      [ OK ]
[19:40:33]   /bin/echo                                       [ OK ]
[19:40:33]   /bin/ed                                         [ OK ]
[19:40:33]   /bin/egrep                                      [ OK ]
[19:40:33] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[19:40:33]   /bin/fgrep                                      [ OK ]
[19:40:33] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[19:40:33]   /bin/fuser                                      [ OK ]
[19:40:33]   /bin/grep                                       [ OK ]
[19:40:34]   /bin/ip                                         [ OK ]
[19:40:34]   /bin/kill                                       [ OK ]
[19:40:34]   /bin/less                                       [ OK ]
[19:40:34]   /bin/login                                      [ OK ]
[19:40:34]   /bin/ls                                         [ OK ]
[19:40:34]   /bin/lsmod                                      [ OK ]
[19:40:34]   /bin/mktemp                                     [ OK ]
[19:40:35]   /bin/more                                       [ OK ]
[19:40:35]   /bin/mount                                      [ OK ]
[19:40:35]   /bin/mv                                         [ OK ]
[19:40:35]   /bin/netstat                                    [ OK ]
[19:40:35]   /bin/ping                                       [ OK ]
[19:40:35]   /bin/ps                                         [ OK ]
[19:40:35]   /bin/pwd                                        [ OK ]
[19:40:35]   /bin/readlink                                   [ OK ]
[19:40:36]   /bin/sed                                        [ OK ]
[19:40:36]   /bin/sh                                         [ OK ]
[19:40:36]   /bin/su                                         [ OK ]
[19:40:36]   /bin/touch                                      [ OK ]
[19:40:36]   /bin/uname                                      [ OK ]
[19:40:37]   /bin/which                                      [ OK ]
[19:40:37] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[19:40:37]   /bin/kmod                                       [ OK ]
[19:40:37]   /bin/dash                                       [ OK ]
[19:41:05]
[19:41:05] Info: Starting test name 'rootkits'
[19:41:05] Checking for rootkits...
[19:41:06]
[19:41:06] Info: Starting test name 'known_rkts'
[19:41:06] Performing check of known rootkit files and directories
[19:41:06]
[19:41:06] Checking for 55808 Trojan - Variant A...
[19:41:06]   Checking for file '/tmp/.../r'                  [ Not found ]
[19:41:06]   Checking for file '/tmp/.../a'                  [ Not found ]
[19:41:06] 55808 Trojan - Variant A                          [ Not found ]
[19:41:06]
[19:41:06] Checking for ADM Worm...
[19:41:06]   Checking for string 'w0rm'                      [ Not found ]
[19:41:06] ADM Worm                                          [ Not found ]
[19:41:06]
[19:41:06] Checking for AjaKit Rootkit...
[19:41:06]   Checking for file '/dev/tux/.addr'              [ Not found ]
[19:41:06]   Checking for file '/dev/tux/.proc'              [ Not found ]
[19:41:06]   Checking for file '/dev/tux/.file'              [ Not found ]
[19:41:06]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[19:41:06]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[19:41:06]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[19:41:06]   Checking for directory '/dev/tux'               [ Not found ]
[19:41:06]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[19:41:06] AjaKit Rootkit                                    [ Not found ]
[19:41:06]
[19:41:06] Checking for Adore Rootkit...
[19:41:06]   Checking for file '/usr/secure'                 [ Not found ]
[19:41:06]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[19:41:06]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[19:41:06]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[19:41:06]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[19:41:06]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[19:41:06]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[19:41:06]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[19:41:06]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[19:41:06]   Checking for file '/var/log/ssh/old'            [ Not found ]
[19:41:06]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[19:41:06]   Checking for directory '/usr/doc/kern'          [ Not found ]
[19:41:07]   Checking for directory '/usr/doc/backup'        [ Not found ]
[19:41:07]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[19:41:07]   Checking for directory '/lib/backup'            [ Not found ]
[19:41:07]   Checking for directory '/lib/backup/txt'        [ Not found ]
[19:41:07]   Checking for directory '/usr/doc/work'          [ Not found ]
[19:41:07]   Checking for directory '/usr/doc/sys'           [ Not found ]
[19:41:07]   Checking for directory '/var/log/ssh'           [ Not found ]
[19:41:07]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[19:41:07]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[19:41:07] Adore Rootkit                                     [ Not found ]
[19:41:07]
[19:41:07] Checking for aPa Kit...
[19:41:07]   Checking for file '/usr/share/.aPa'             [ Not found ]
[19:41:07] aPa Kit                                           [ Not found ]
[19:41:07]
[19:41:07] Checking for Apache Worm...
[19:41:07]   Checking for file '/bin/.log'                   [ Not found ]
[19:41:07] Apache Worm                                       [ Not found ]
[19:41:07]
[19:41:07] Checking for Ambient (ark) Rootkit...
[19:41:07]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[19:41:07]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[19:41:07]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[19:41:07]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[19:41:07]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[19:41:07]   Checking for directory '/dev/ptyxx'             [ Not found ]
[19:41:07] Ambient (ark) Rootkit                             [ Not found ]
[19:41:07]
[19:41:07] Checking for Balaur Rootkit...
[19:41:07]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[19:41:07]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[19:41:07]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[19:41:07]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[19:41:07] Balaur Rootkit                                    [ Not found ]
[19:41:07]
[19:41:07] Checking for BeastKit Rootkit...
[19:41:08]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[19:41:08]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[19:41:08]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[19:41:08]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[19:41:08] BeastKit Rootkit                                  [ Not found ]
[19:41:08]
[19:41:08] Checking for beX2 Rootkit...
[19:41:08]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[19:41:08]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[19:41:08]   Checking for directory '/usr/include/bex'       [ Not found ]
[19:41:08] beX2 Rootkit                                      [ Not found ]
[19:41:08]
[19:41:08] Checking for BOBKit Rootkit...
[19:41:08]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[19:41:08]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[19:41:08]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[19:41:08]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[19:41:08]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[19:41:08]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[19:41:08]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[19:41:08]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[19:41:08]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[19:41:08]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../find'           [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../du'             [ Not found ]
[19:41:09]   Checking for file '/usr/lib/.../top'            [ Not found ]
[19:41:09]   Checking for directory '/usr/sbin/...'          [ Not found ]
[19:41:09]   Checking for directory '/usr/include/...'       [ Not found ]
[19:41:09]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[19:41:09]   Checking for directory '/usr/lib/...'           [ Not found ]
[19:41:09]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[19:41:09]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[19:41:09]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[19:41:09]   Checking for directory '/tmp/.bkp'              [ Not found ]
[19:41:09] BOBKit Rootkit                                    [ Not found ]
[19:41:09]
[19:41:09] Checking for cb Rootkit...
[19:41:09]   Checking for file '/dev/srd0'                   [ Not found ]
[19:41:09]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[19:41:09]   Checking for file '/dev/mounnt'                 [ Not found ]
[19:41:09]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[19:41:09]   Checking for file '/usr/bin/.zeen/.. /cl'       [ Not found ]
[19:41:09]   Checking for file '/usr/bin/.zeen/.. /.x.tgz'   [ Not found ]
[19:41:09]   Checking for file '/usr/bin/.zeen/.. /statdx'   [ Not found ]
[19:41:09]   Checking for file '/usr/bin/.zeen/.. /wted'     [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /write'    [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /scan'     [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /sc'       [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /sl2'      [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /wroot'    [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /wscan'    [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /wu'       [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /v'        [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /read'     [ Not found ]
[19:41:10]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[19:41:10]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[19:41:10]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[19:41:10]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[19:41:10]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[19:41:10]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[19:41:10]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[19:41:10]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.system/.. /tcp.log' [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /curatare/attrib' [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /curatare/chattr' [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /curatare/ps' [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.zeen/.. /curatare/pstree' [ Not found ]
[19:41:10]   Checking for file '/usr/bin/.system/.. /.x/xC.o' [ Not found ]
[19:41:10]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[19:41:10]   Checking for directory '/usr/bin/.zeen/.. /curatare' [ Not found ]
[19:41:10]   Checking for directory '/usr/bin/.zeen/.. /scan' [ Not found ]
[19:41:10]   Checking for directory '/usr/bin/.system/.. '   [ Not found ]
[19:41:10] cb Rootkit                                        [ Not found ]
[19:41:10]
[19:41:10] Checking for CiNIK Worm (Slapper.B variant)...
[19:41:10]   Checking for file '/tmp/.cinik'                 [ Not found ]
[19:41:10]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[19:41:11] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[19:41:11]
[19:41:11] Checking for Danny-Boy's Abuse Kit...
[19:41:11]   Checking for file '/dev/mdev'                   [ Not found ]
[19:41:11]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[19:41:11] Danny-Boy's Abuse Kit                             [ Not found ]
[19:41:11]
[19:41:11] Checking for Devil RootKit...
[19:41:11]   Checking for file '/var/lib/games/.src'         [ Not found ]
[19:41:11]   Checking for file '/dev/dsx'                    [ Not found ]
[19:41:11]   Checking for file '/dev/caca'                   [ Not found ]
[19:41:11]   Checking for file '/dev/pro'                    [ Not found ]
[19:41:11]   Checking for file '/bin/bye'                    [ Not found ]
[19:41:11]   Checking for file '/bin/homedir'                [ Not found ]
[19:41:11]   Checking for file '/usr/bin/xfss'               [ Not found ]
[19:41:11]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[19:41:11]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[19:41:12]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[19:41:12]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[19:41:12] Devil RootKit                                     [ Not found ]
[19:41:12]
[19:41:12] Checking for Dica-Kit Rootkit...
[19:41:12]   Checking for file '/lib/.sso'                   [ Not found ]
[19:41:12]   Checking for file '/lib/.so'                    [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/read'       [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/write'      [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/va'         [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[19:41:12]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[19:41:12]   Checking for file '/usr/bin/.etc'               [ Not found ]
[19:41:12]   Checking for file '/etc/sshd_config'            [ Not found ]
[19:41:12]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[19:41:12]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[19:41:12]   Checking for directory '/var/run/...dica'       [ Not found ]
[19:41:12]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[19:41:12]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[19:41:12] Dica-Kit Rootkit                                  [ Not found ]
[19:41:12]
[19:41:12] Checking for Dreams Rootkit...
[19:41:12]   Checking for file '/dev/ttyoa'                  [ Not found ]
[19:41:12]   Checking for file '/dev/ttyof'                  [ Not found ]
[19:41:12]   Checking for file '/dev/ttyop'                  [ Not found ]
[19:41:13]   Checking for file '/usr/bin/sense'              [ Not found ]
[19:41:13]   Checking for file '/usr/bin/sl2'                [ Not found ]
[19:41:13]   Checking for file '/usr/bin/logclear'           [ Not found ]
[19:41:13]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[19:41:13]   Checking for file '/usr/bin/initrd'             [ Not found ]
[19:41:13]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[19:41:13]   Checking for file '/usr/bin/snfs'               [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libsss'             [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[19:41:13]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[19:41:13]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[19:41:13]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[19:41:13]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[19:41:13]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[19:41:13]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[19:41:13]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[19:41:13]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[19:41:13]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[19:41:13]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[19:41:13]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[19:41:13] Dreams Rootkit                                    [ Not found ]
[19:41:13]
[19:41:13] Checking for Duarawkz Rootkit...
[19:41:13]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[19:41:13]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[19:41:13] Duarawkz Rootkit                                  [ Not found ]
[19:41:13]
[19:41:13] Checking for Enye LKM...
[19:41:14]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[19:41:14]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[19:41:14] Enye LKM                                          [ Not found ]
[19:41:14]
[19:41:14] Checking for Flea Linux Rootkit...
[19:41:14]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[19:41:14]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[19:41:14]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[19:41:14]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[19:41:14]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[19:41:14]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[19:41:14]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[19:41:14]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[19:41:14]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[19:41:14]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[19:41:14]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[19:41:14]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[19:41:14]   Checking for directory '/dev/..0'               [ Not found ]
[19:41:14]   Checking for directory '/dev/..0/backup'        [ Not found ]
[19:41:14] Flea Linux Rootkit                                [ Not found ]
[19:41:14]
[19:41:14] Checking for Fu Rootkit...
[19:41:14]   Checking for file '/sbin/xc'                    [ Not found ]
[19:41:14]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[19:41:14]   Checking for file '/bin/.lib'                   [ Not found ]
[19:41:14] Fu Rootkit                                        [ Not found ]
[19:41:14]
[19:41:14] Checking for ****`it Rootkit...
[19:41:14]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[19:41:14]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[19:41:14]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[19:41:14]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[19:41:14]   Checking for file '/dev/proc/****it/hax0r'      [ Not found ]
[19:41:14]   Checking for file '/dev/proc/****it/hax0rshell' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/config/lports' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/config/rports' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/config/rkconf' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/config/password' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/config/progs' [ Not found ]
[19:41:15]   Checking for file '/dev/proc/****it/system-bins/init' [ Not found ]
[19:41:15]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[19:41:15]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[19:41:15]   Checking for directory '/dev/proc'              [ Not found ]
[19:41:15]   Checking for directory '/dev/proc/****it'       [ Not found ]
[19:41:15]   Checking for directory '/dev/proc/****it/system-bins' [ Not found ]
[19:41:15]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[19:41:15] ****`it Rootkit                                   [ Not found ]
[19:41:15]
[19:41:15] Checking for GasKit Rootkit...
[19:41:15]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[19:41:15]   Checking for directory '/dev/dev'               [ Not found ]
[19:41:15]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[19:41:15]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[19:41:15] GasKit Rootkit                                    [ Not found ]
[19:41:15]
[19:41:15] Checking for Heroin LKM...
[19:41:15]   Checking for kernel symbol 'heroin'             [ Not found ]
[19:41:15] Heroin LKM                                        [ Not found ]
[19:41:15]
[19:41:15] Checking for HjC Kit...
[19:41:15]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[19:41:15] HjC Kit                                           [ Not found ]
[19:41:15]
[19:41:15] Checking for ignoKit Rootkit...
[19:41:15]   Checking for file '/lib/defs/p'                 [ Not found ]
[19:41:15]   Checking for file '/lib/defs/q'                 [ Not found ]
[19:41:15]   Checking for file '/lib/defs/r'                 [ Not found ]
[19:41:16]   Checking for file '/lib/defs/s'                 [ Not found ]
[19:41:16]   Checking for file '/lib/defs/t'                 [ Not found ]
[19:41:16]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[19:41:16]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[19:41:16]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[19:41:16]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[19:41:16]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[19:41:16]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[19:41:16]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[19:41:16]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[19:41:16]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[19:41:16] ignoKit Rootkit                                   [ Not found ]
[19:41:16]
[19:41:16] Checking for IntoXonia-NG Rootkit...
[19:41:16]   Checking for kernel symbol 'funces'             [ Not found ]
[19:41:16]   Checking for kernel symbol 'ixinit'             [ Not found ]
[19:41:16]   Checking for kernel symbol 'tricks'             [ Not found ]
[19:41:16]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[19:41:17]   Checking for kernel symbol 'rootme'             [ Not found ]
[19:41:17]   Checking for kernel symbol 'hide_module'        [ Not found ]
[19:41:17]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[19:41:17] IntoXonia-NG Rootkit                              [ Not found ]
[19:41:17]
[19:41:17] Checking for Irix Rootkit...
[19:41:17]   Checking for directory '/dev/pts/01'            [ Not found ]
[19:41:17]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[19:41:17]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[19:41:17]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[19:41:17] Irix Rootkit                                      [ Not found ]
[19:41:17]
[19:41:17] Checking for Jynx Rootkit...
[19:41:17]   Checking for file '/xochikit/bc'                [ Not found ]
[19:41:17]   Checking for file '/xochikit/ld_poison.so'      [ Not found ]
[19:41:17]   Checking for file '/omgxochi/bc'                [ Not found ]
[19:41:17]   Checking for file '/omgxochi/ld_poison.so'      [ Not found ]
[19:41:17]   Checking for directory '/xochikit'              [ Not found ]
[19:41:17]   Checking for directory '/omgxochi'              [ Not found ]
[19:41:17] Jynx Rootkit                                      [ Not found ]
[19:41:17]
[19:41:17] Checking for KBeast Rootkit...
[19:41:17]   Checking for file '/usr/_h4x_/ipsecs-kbeast-v1.ko' [ Not found ]
[19:41:17]   Checking for file '/usr/_h4x_/_h4x_bd'          [ Not found ]
[19:41:18]   Checking for file '/usr/_h4x_/acctlog'          [ Not found ]
[19:41:18]   Checking for directory '/usr/_h4x_'             [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_delete_module'  [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_getdents64'     [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_kill'           [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_open'           [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_read'           [ Not found ]
[19:41:18]   Checking for kernel symbol 'h4x_rename'         [ Not found ]
[19:41:19]   Checking for kernel symbol 'h4x_rmdir'          [ Not found ]
[19:41:19]   Checking for kernel symbol 'h4x_tcp4_seq_show'  [ Not found ]
[19:41:19]   Checking for kernel symbol 'h4x_write'          [ Not found ]
[19:41:19] KBeast Rootkit                                    [ Not found ]
[19:41:19]
[19:41:19] Checking for Kitko Rootkit...
[19:41:19]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[19:41:19] Kitko Rootkit                                     [ Not found ]
[19:41:19]
[19:41:19] Checking for Knark Rootkit...
[19:41:19]   Checking for file '/proc/knark/pids'            [ Not found ]
[19:41:19]   Checking for directory '/proc/knark'            [ Not found ]
[19:41:19] Knark Rootkit                                     [ Not found ]
[19:41:19]
[19:41:19] Checking for ld-linuxv.so Rootkit...
[19:41:19]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[19:41:19]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[19:41:19]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[19:41:19]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[19:41:19] ld-linuxv.so Rootkit                              [ Not found ]
[19:41:19]
[19:41:19] Checking for Li0n Worm...
[19:41:19]   Checking for file '/bin/in.telnetd'             [ Not found ]
[19:41:19]   Checking for file '/bin/mjy'                    [ Not found ]
[19:41:19]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[19:41:19]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[19:41:19]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[19:41:19]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[19:41:19]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[19:41:19]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[19:41:20]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[19:41:20] Li0n Worm                                         [ Not found ]
[19:41:20]
[19:41:20] Checking for Lockit / LJK2 Rootkit...
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[19:41:20]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[19:41:21]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[19:41:21]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[19:41:21] Lockit / LJK2 Rootkit                             [ Not found ]
[19:41:21]
[19:41:21] Checking for Mood-NT Rootkit...
[19:41:21]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[19:41:21]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[19:41:21]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[19:41:21]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[19:41:21]   Checking for directory '/_cthulhu'              [ Not found ]
[19:41:21] Mood-NT Rootkit                                   [ Not found ]
[19:41:21]
[19:41:21] Checking for MRK Rootkit...
[19:41:21]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[19:41:21]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[19:41:21]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[19:41:21]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[19:41:21]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[19:41:22]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[19:41:22] MRK Rootkit                                       [ Not found ]
[19:41:22]
[19:41:22] Checking for Ni0 Rootkit...
[19:41:22]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[19:41:22]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[19:41:22]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[19:41:22]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[19:41:22]   Checking for directory '/tmp/waza'              [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[19:41:22]   Checking for directory '/usr/sbin/es'           [ Not found ]
[19:41:22] Ni0 Rootkit                                       [ Not found ]
[19:41:22]
[19:41:22] Checking for Ohhara Rootkit...
[19:41:22]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[19:41:22]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[19:41:22] Ohhara Rootkit                                    [ Not found ]
[19:41:22]
[19:41:22] Checking for Optic Kit (Tux) Worm...
[19:41:22]   Checking for directory '/dev/tux'               [ Not found ]
[19:41:22]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[19:41:22]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[19:41:22]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[19:41:22] Optic Kit (Tux) Worm                              [ Not found ]
[19:41:22]
[19:41:22] Checking for Oz Rootkit...
[19:41:22]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[19:41:22]   Checking for directory '/dev/.oz'               [ Not found ]
[19:41:22] Oz Rootkit                                        [ Not found ]
[19:41:22]
[19:41:22] Checking for Phalanx Rootkit...
[19:41:22]   Checking for file '/uNFuNF'                     [ Not found ]
[19:41:23]   Checking for file '/etc/host.ph1'               [ Not found ]
[19:41:23]   Checking for file '/bin/host.ph1'               [ Not found ]
[19:41:23]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[19:41:23]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[19:41:23]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[19:41:23]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[19:41:23]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[19:41:23] Phalanx Rootkit                                   [ Not found ]
[19:41:23]
[19:41:23] Checking for Phalanx2 Rootkit...
[19:41:23]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[19:41:23]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[19:41:23]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[19:41:23]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[19:41:23]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[19:41:23]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[19:41:23]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[19:41:23]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[19:41:23]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[19:41:23]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[19:41:23]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[19:41:23]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[19:41:23]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[19:41:23]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[19:41:23] Phalanx2 Rootkit                                  [ Not found ]
[19:41:23]
[19:41:23] Checking for Phalanx2 Rootkit (extended tests)...
[19:41:23]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[19:41:23]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[19:41:23]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[19:41:23] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[19:41:23]
[19:41:23] Checking for Portacelo Rootkit...
[19:41:23]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../.p'             [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../getty'          [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../show'           [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[19:41:24]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[19:41:24]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[19:41:24] Portacelo Rootkit                                 [ Not found ]
[19:41:24]
[19:41:24] Checking for R3dstorm Toolkit...
[19:41:24]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[19:41:24]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[19:41:24]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[19:41:24]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[19:41:24]   Checking for file '/bin/.../see_all'            [ Not found ]
[19:41:24]   Checking for directory '/var/log/tk02'          [ Not found ]
[19:41:24]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[19:41:24]   Checking for directory '/bin/...'               [ Not found ]
[19:41:24] R3dstorm Toolkit                                  [ Not found ]
[19:41:24]
[19:41:24] Checking for RH-Sharpe's Rootkit...
[19:41:24]   Checking for file '/bin/lps'                    [ Not found ]
[19:41:24]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[19:41:24]   Checking for file '/usr/bin/ltop'               [ Not found ]
[19:41:24]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[19:41:24]   Checking for file '/usr/bin/ldu'                [ Not found ]
[19:41:24]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[19:41:24]   Checking for file '/usr/bin/wp'                 [ Not found ]
[19:41:25]   Checking for file '/usr/bin/shad'               [ Not found ]
[19:41:25]   Checking for file '/usr/bin/vadim'              [ Not found ]
[19:41:25]   Checking for file '/usr/bin/slice'              [ Not found ]
[19:41:25]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[19:41:25]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[19:41:25] RH-Sharpe's Rootkit                               [ Not found ]
[19:41:25]
[19:41:25] Checking for RSHA's Rootkit...
[19:41:25]   Checking for file '/bin/kr4p'                   [ Not found ]
[19:41:25]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[19:41:25]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[19:41:25]   Checking for file '/usr/bin/slice2'             [ Not found ]
[19:41:25]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[19:41:25]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[19:41:25]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[19:41:25]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[19:41:25] RSHA's Rootkit                                    [ Not found ]
[19:41:25]
[19:41:25] Checking for Scalper Worm...
[19:41:25]   Checking for file '/tmp/.a'                     [ Not found ]
[19:41:25]   Checking for file '/tmp/.uua'                   [ Not found ]
[19:41:25] Scalper Worm                                      [ Not found ]
[19:41:25]
[19:41:25] Checking for Sebek LKM...
[19:41:26]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[19:41:26] Sebek LKM                                         [ Not found ]
[19:41:26]
[19:41:26] Checking for Shutdown Rootkit...
[19:41:26]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[19:41:26]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[19:41:26]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[19:41:26]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[19:41:26]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[19:41:26]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[19:41:26]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[19:41:26]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[19:41:26] Shutdown Rootkit                                  [ Not found ]
[19:41:26]
[19:41:26] Checking for SHV4 Rootkit...
[19:41:26]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[19:41:26]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[19:41:26]   Checking for file '/lib/lidps1.so'              [ Not found ]
[19:41:26]   Checking for file '/lib/libproc.a'              [ Not found ]
[19:41:26]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[19:41:26]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[19:41:27]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[19:41:27]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[19:41:27]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[19:41:27]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[19:41:27]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[19:41:27]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[19:41:27]   Checking for file '/usr/include/file.h'         [ Not found ]
[19:41:27]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[19:41:27]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[19:41:27]   Checking for file '/usr/include/log.h'          [ Not found ]
[19:41:27]   Checking for file '/usr/include/proc.h'         [ Not found ]
[19:41:27]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[19:41:27]   Checking for file '/dev/srd0'                   [ Not found ]
[19:41:27]   Checking for directory '/lib/ldd.so'            [ Not found ]
[19:41:27]   Checking for directory '/lib/security/.config'  [ Not found ]
[19:41:27]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[19:41:27] SHV4 Rootkit                                      [ Not found ]
[19:41:27]
[19:41:27] Checking for SHV5 Rootkit...
[19:41:27]   Checking for file '/etc/sh.conf'                [ Not found ]
[19:41:27]   Checking for file '/lib/libproc.a'              [ Not found ]
[19:41:27]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[19:41:27]   Checking for file '/lib/lidps1.so'              [ Not found ]
[19:41:27]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[19:41:27]   Checking for file '/usr/include/file.h'         [ Not found ]
[19:41:27]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[19:41:27]   Checking for file '/usr/include/log.h'          [ Not found ]
[19:41:27]   Checking for file '/usr/include/proc.h'         [ Not found ]
[19:41:27]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[19:41:27]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[19:41:27]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[19:41:27]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[19:41:28]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[19:41:28]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[19:41:28]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[19:41:28]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[19:41:28]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[19:41:28]   Checking for file '/dev/srd0'                   [ Not found ]
[19:41:28]   Checking for directory '/lib/libsh.so'          [ Not found ]
[19:41:28]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[19:41:28]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[19:41:28]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[19:41:28] SHV5 Rootkit                                      [ Not found ]
[19:41:28]
[19:41:28] Checking for Sin Rootkit...
[19:41:28]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[19:41:28]   Checking for file '/dev/ttyoa'                  [ Not found ]
[19:41:28]   Checking for file '/dev/ttyof'                  [ Not found ]
[19:41:28]   Checking for file '/dev/ttyop'                  [ Not found ]
[19:41:28]   Checking for file '/dev/ttyos'                  [ Not found ]
[19:41:28]   Checking for file '/usr/lib/.lib'               [ Not found ]
[19:41:28]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[19:41:28]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[19:41:28]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[19:41:28]   Checking for file '/usr/man/man1/...'           [ Not found ]
[19:41:28]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[19:41:28]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[19:41:28]   Checking for directory '/usr/lib/sn'            [ Not found ]
[19:41:28]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[19:41:28]   Checking for directory '/dev/.haos'             [ Not found ]
[19:41:28] Sin Rootkit                                       [ Not found ]
[19:41:28]
[19:41:28] Checking for Slapper Worm...
[19:41:28]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[19:41:28]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[19:41:29]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[19:41:29]   Checking for file '/tmp/httpd'                  [ Not found ]
[19:41:29]   Checking for file '/tmp/.unlock'                [ Not found ]
[19:41:29]   Checking for file '/tmp/update'                 [ Not found ]
[19:41:29]   Checking for file '/tmp/.cinik'                 [ Not found ]
[19:41:29]   Checking for file '/tmp/.b'                     [ Not found ]
[19:41:29] Slapper Worm                                      [ Not found ]
[19:41:29]
[19:41:29] Checking for Sneakin Rootkit...
[19:41:29]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[19:41:29] Sneakin Rootkit                                   [ Not found ]
[19:41:29]
[19:41:29] Checking for 'Spanish' Rootkit...
[19:41:29]   Checking for file '/dev/ptyq'                   [ Not found ]
[19:41:29]   Checking for file '/bin/ad'                     [ Not found ]
[19:41:29]   Checking for file '/bin/ava'                    [ Not found ]
[19:41:29]   Checking for file '/bin/server'                 [ Not found ]
[19:41:29]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[19:41:29]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[19:41:29]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[19:41:29]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[19:41:29]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[19:41:29]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[19:41:29]   Checking for directory '/usr/share/...'         [ Not found ]
[19:41:29] 'Spanish' Rootkit                                 [ Not found ]
[19:41:30]
[19:41:30] Checking for Suckit Rootkit...
[19:41:30]   Checking for file '/sbin/initsk12'              [ Not found ]
[19:41:30]   Checking for file '/sbin/initxrk'               [ Not found ]
[19:41:30]   Checking for file '/usr/bin/null'               [ Not found ]
[19:41:30]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[19:41:30]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[19:41:30]   Checking for directory '/etc/.MG'               [ Not found ]
[19:41:30]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[19:41:30]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[19:41:30] Suckit Rootkit                                    [ Not found ]
[19:41:30]
[19:41:30] Checking for Superkit Rootkit...
[19:41:30]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[19:41:30]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[19:41:30]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[19:41:30]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[19:41:30]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[19:41:30] Superkit Rootkit                                  [ Not found ]
[19:41:30]
[19:41:30] Checking for TBD (Telnet BackDoor)...
[19:41:30]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[19:41:30] TBD (Telnet BackDoor)                             [ Not found ]
[19:41:30]
[19:41:30] Checking for TeLeKiT Rootkit...
[19:41:30]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[19:41:30]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[19:41:30]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[19:41:30]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[19:41:31]   Checking for file '/dev/ptyr'                   [ Not found ]
[19:41:31]   Checking for file '/dev/ptyp'                   [ Not found ]
[19:41:31]   Checking for file '/dev/ptyq'                   [ Not found ]
[19:41:31]   Checking for file '/dev/hda06'                  [ Not found ]
[19:41:31]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[19:41:31]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[19:41:31]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[19:41:31]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[19:41:31] TeLeKiT Rootkit                                   [ Not found ]
[19:41:31]
[19:41:31] Checking for T0rn Rootkit...
[19:41:31]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[19:41:31]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[19:41:32]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[19:41:32]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[19:41:32]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[19:41:32]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[19:41:32]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[19:41:32]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[19:41:32]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[19:41:32]   Checking for directory '/dev/.lib'              [ Not found ]
[19:41:32]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[19:41:32]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[19:41:32]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[19:41:32]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[19:41:32]   Checking for directory '/usr/src/.puta'         [ Not found ]
[19:41:32]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[19:41:32]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[19:41:32]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[19:41:32]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[19:41:32] T0rn Rootkit                                      [ Not found ]
[19:41:32]
[19:41:32] Checking for trNkit Rootkit...
[19:41:32]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[19:41:32]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[19:41:32]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[19:41:33]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[19:41:33]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[19:41:33]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[19:41:33]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[19:41:33] trNkit Rootkit                                    [ Not found ]
[19:41:33]
[19:41:33] Checking for Trojanit Kit...
[19:41:33]   Checking for file '/bin/.ls'                    [ Not found ]
[19:41:33]   Checking for file '/bin/.ps'                    [ Not found ]
[19:41:33]   Checking for file '/bin/.netstat'               [ Not found ]
[19:41:33]   Checking for file '/usr/bin/.nop'               [ Not found ]
[19:41:33]   Checking for file '/usr/bin/.who'               [ Not found ]
[19:41:33] Trojanit Kit                                      [ Not found ]
[19:41:33]
[19:41:33] Checking for Tuxtendo Rootkit...
[19:41:33]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[19:41:33]   Checking for file '/usr/bin/xchk'               [ Not found ]
[19:41:33]   Checking for file '/usr/bin/xsf'                [ Not found ]
[19:41:33]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.addr'              [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.cron'              [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.file'              [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.log'               [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.proc'              [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.iface'             [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.pw'                [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.df'                [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[19:41:33]   Checking for file '/dev/tux/.tux'               [ Not found ]
[19:41:33]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[19:41:33]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[19:41:33]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[19:41:33]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[19:41:34]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[19:41:34]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[19:41:34]   Checking for directory '/dev/tux'               [ Not found ]
[19:41:34]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[19:41:34]   Checking for directory '/dev/tux/backup'        [ Not found ]
[19:41:34] Tuxtendo Rootkit                                  [ Not found ]
[19:41:34]
[19:41:34] Checking for URK Rootkit...
[19:41:34]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[19:41:34]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[19:41:34]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[19:41:34]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[19:41:35]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[19:41:35]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[19:41:35]   Checking for file '/tmp/conf.inv'               [ Not found ]
[19:41:35]   Checking for directory '/dev/prom'              [ Not found ]
[19:41:35]   Checking for directory '/dev/pts/01'            [ Not found ]
[19:41:35]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[19:41:35]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[19:41:35] URK Rootkit                                       [ Not found ]
[19:41:35]
[19:41:35] Checking for Vampire Rootkit...
[19:41:35]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[19:41:36]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[19:41:36]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[19:41:36]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[19:41:36] Vampire Rootkit                                   [ Not found ]
[19:41:36]
[19:41:36] Checking for VcKit Rootkit...
[19:41:36]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[19:41:36]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[19:41:36] VcKit Rootkit                                     [ Not found ]
[19:41:36]
[19:41:36] Checking for Volc Rootkit...
[19:41:36]   Checking for file '/usr/bin/volc'               [ Not found ]
[19:41:36]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[19:41:36]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[19:41:36]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[19:41:36]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[19:41:36]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[19:41:36]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[19:41:36]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[19:41:36]   Checking for directory '/var/spool/.recent'     [ Not found ]
[19:41:36]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[19:41:36]   Checking for directory '/usr/lib/volc'          [ Not found ]
[19:41:36]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[19:41:36] Volc Rootkit                                      [ Not found ]
[19:41:36]
[19:41:36] Checking for Xzibit Rootkit...
[19:41:36]   Checking for file '/dev/dsx'                    [ Not found ]
[19:41:36]   Checking for file '/dev/caca'                   [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[19:41:36]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[19:41:37]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[19:41:37]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[19:41:37]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[19:41:37]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[19:41:37]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[19:41:37]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[19:41:37]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[19:41:37]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[19:41:37]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[19:41:37]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[19:41:37] Xzibit Rootkit                                    [ Not found ]
[19:41:37]
[19:41:37] Checking for zaRwT.KiT Rootkit...
[19:41:37]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[19:41:37]   Checking for file '/dev/ttyf'                   [ Not found ]
[19:41:37]   Checking for file '/dev/ttyp'                   [ Not found ]
[19:41:37]   Checking for file '/dev/ttyn'                   [ Not found ]
[19:41:37]   Checking for file '/rk/tulz'                    [ Not found ]
[19:41:37]   Checking for directory '/rk'                    [ Not found ]
[19:41:37]   Checking for directory '/dev/rd/s'              [ Not found ]
[19:41:37] zaRwT.KiT Rootkit                                 [ Not found ]
[19:41:37]
[19:41:37] Checking for ZK Rootkit...
[19:41:37]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[19:41:37]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[19:41:37]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[19:41:37]   Checking for file '/etc/1ssue.net'              [ Not found ]
[19:41:37]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[19:41:37]   Checking for directory '/usr/share/.zk'         [ Not found ]
[19:41:37]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[19:41:37] ZK Rootkit                                        [ Not found ]
[19:41:39]
[19:41:39] Info: Starting test name 'additional_rkts'
[19:41:39] Performing additional rootkit checks
[19:41:39]
[19:41:39]   Performing Suckit Rookit additional checks
[19:41:39]     Checking hard link count on '/sbin/init'      [ OK ]
[19:41:39]     Checking for hidden file extensions           [ None found ]
[19:41:39]     Running skdet command                         [ Skipped ]
[19:41:39] Info: Unable to find the 'skdet' command
[19:41:39]   Suckit Rookit additional checks                 [ OK ]
[19:41:39]
[19:41:39] Info: Starting test name 'possible_rkt_files'
[19:41:39]   Performing check of possible rootkit files and directories
[19:41:39]     Checking for file '/dev/sdr0'                 [ Not found ]
[19:41:39]     Checking for file '/dev/pisu'                 [ Not found ]
[19:41:39]     Checking for file '/dev/xdta'                 [ Not found ]
[19:41:39]     Checking for file '/dev/saux'                 [ Not found ]
[19:41:39]     Checking for file '/dev/hdx'                  [ Not found ]
[19:41:39]     Checking for file '/dev/hdx1'                 [ Not found ]
[19:41:39]     Checking for file '/dev/hdx2'                 [ Not found ]
[19:41:39]     Checking for file '/dev/ptyy'                 [ Not found ]
[19:41:39]     Checking for file '/dev/ptyu'                 [ Not found ]
[19:41:39]     Checking for file '/dev/ptyv'                 [ Not found ]
[19:41:39]     Checking for file '/dev/hdbb'                 [ Not found ]
[19:41:40]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[19:41:40]     Checking for file '/tmp/.bash_history'        [ Not found ]
[19:41:40]     Checking for file '/usr/info/.clib'           [ Not found ]
[19:41:40]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[19:41:40]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[19:41:40]     Checking for file '/sbin/create'              [ Not found ]
[19:41:40]     Checking for file '/dev/ttypz'                [ Not found ]
[19:41:40]     Checking for file '/var/log/tcp.log'          [ Not found ]
[19:41:40]     Checking for file '/usr/include/audit.h'      [ Not found ]
[19:41:40]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[19:41:40]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[19:41:40]     Checking for file '/dev/xmx'                  [ Not found ]
[19:41:40]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[19:41:40]     Checking for file '/bin/vobiscum'             [ Not found ]
[19:41:40]     Checking for file '/bin/psr'                  [ Not found ]
[19:41:40]     Checking for file '/dev/kdx'                  [ Not found ]
[19:41:40]     Checking for file '/dev/dkx'                  [ Not found ]
[19:41:40]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[19:41:40]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[19:41:40]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[19:41:40]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[19:41:40]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[19:41:40]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[19:41:41]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[19:41:41]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[19:41:41]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[19:41:41]     Checking for file '/tmp/.ush'                 [ Not found ]
[19:41:41]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[19:41:41]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[19:41:41]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[19:41:41]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[19:41:41]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[19:41:41]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[19:41:41]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[19:41:41]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[19:41:41]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[19:41:41]     Checking for file '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:41]     Checking for file '/etc/init.d/xfs3'          [ Not found ]
[19:41:41]     Checking for file '/usr/sbin/t.txt'           [ Not found ]
[19:41:41]     Checking for file '/usr/sbin/change'          [ Not found ]
[19:41:41]     Checking for file '/usr/sbin/s'               [ Not found ]
[19:41:41]     Checking for file '/bin/f'                    [ Not found ]
[19:41:41]     Checking for file '/bin/i'                    [ Not found ]
[19:41:41]     Checking for file '/lib/libncom.so.4.0.1'     [ Not found ]
[19:41:41]     Checking for file '/sbin/zinit'               [ Not found ]
[19:41:41]     Checking for file '/tmp/pass_ssh.log'         [ Not found ]
[19:41:41]     Checking for file '/usr/include/gpm2.h'       [ Not found ]
[19:41:41]     Checking for file '/etc/ssh/.sshd_auth'       [ Not found ]
[19:41:41]     Checking for file '/usr/lib/.sshd.h'          [ Not found ]
[19:41:41]     Checking for file '/var/run/.defunct'         [ Not found ]
[19:41:41]     Checking for file '/etc/httpd/run/.defunct'   [ Not found ]
[19:41:41]     Checking for file '/usr/share/pci.r'          [ Not found ]
[19:41:41]     Checking for file '/etc/cron.daily/dnsquery'  [ Not found ]
[19:41:42]     Checking for file '/usr/lib/libutil1.2.1.2.so' [ Not found ]
[19:41:42]     Checking for file '/bin/ceva'                 [ Not found ]
[19:41:42]     Checking for file '/sbin/syslogd '            [ Not found ]
[19:41:42]     Checking for file '/usr/include/shup.h'       [ Not found ]
[19:41:42]     Checking for file '/etc/rpm/sshdOLD'          [ Not found ]
[19:41:42]     Checking for file '/etc/rpm/sshOLD'           [ Not found ]
[19:41:42]     Checking for file '/usr/share/passwd.h'       [ Not found ]
[19:41:42]     Checking for file '/lib/.xsyslog'             [ Not found ]
[19:41:42]     Checking for file '/etc/.xsyslog'             [ Not found ]
[19:41:42]     Checking for file '/lib/.ssyslog'             [ Not found ]
[19:41:42]     Checking for file '/tmp/.sendmail'            [ Not found ]
[19:41:42]     Checking for file '/usr/share/sshd.sync'      [ Not found ]
[19:41:42]     Checking for file '/bin/zcut'                 [ Not found ]
[19:41:42]     Checking for file '/usr/bin/zmuie'            [ Not found ]
[19:41:42]     Checking for directory '/dev/ptyas'           [ Not found ]
[19:41:42]     Checking for directory '/usr/bin/take'        [ Not found ]
[19:41:42]     Checking for directory '/usr/src/.lib'        [ Not found ]
[19:41:42]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[19:41:42]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[19:41:42]     Checking for directory '/usr/sbin/...'        [ Not found ]
[19:41:42]     Checking for directory '/usr/share/.gun'      [ Not found ]
[19:41:42]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[19:41:42]     Checking for directory '/usr/man/man1/..  /.dir' [ Not found ]
[19:41:42]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[19:41:42]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[19:41:42]     Checking for directory '/tmp/.sys'            [ Not found ]
[19:41:42]     Checking for directory '/tmp/''               [ Not found ]
[19:41:42]     Checking for directory '/tmp/.,'              [ Not found ]
[19:41:42]     Checking for directory '/tmp/,.,'             [ Not found ]
[19:41:42]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[19:41:42]     Checking for directory '/var/tmp/.log'        [ Not found ]
[19:41:43]     Checking for directory '/tmp/zmeu/... '       [ Not found ]
[19:41:43]     Checking for directory '/var/log/ssh'         [ Not found ]
[19:41:43]     Checking for directory '/dev/ida'             [ Not found ]
[19:41:43]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[19:41:43]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[19:41:43]     Checking for directory '/usr/src/.poop'       [ Not found ]
[19:41:43]     Checking for directory '/dev/wd4'             [ Not found ]
[19:41:43]     Checking for directory '/var/run/.tmp'        [ Not found ]
[19:41:43]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[19:41:43]     Checking for directory '/dev/portd'           [ Not found ]
[19:41:43]     Checking for directory '/dev/...'             [ Not found ]
[19:41:43]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[19:41:43]     Checking for directory '/lib/.so'             [ Not found ]
[19:41:43]     Checking for directory '/lib/.sso'            [ Not found ]
[19:41:43]     Checking for directory '/usr/include/sslv3'   [ Not found ]
[19:41:43]     Checking for directory '/dev/shm/sshd'        [ Not found ]
[19:41:43]     Checking for directory '/usr/share/locale/mk/.dev/sk' [ Not found ]
[19:41:43]     Checking for directory '/usr/share/locale/mk/.dev' [ Not found ]
[19:41:43]     Checking for directory '/usr/include/netda.h' [ Not found ]
[19:41:43]     Checking for directory '/usr/include/.ssh'    [ Not found ]
[19:41:43]     Checking for directory '/usr/share/locale/jp/. ' [ Not found ]
[19:41:43]     Checking for directory '/usr/share/.sqe'      [ Not found ]
[19:41:43]   Checking for possible rootkit files and directories [ None found ]
[19:41:43]
[19:41:43] Info: Starting test name 'possible_rkt_strings'
[19:41:43]   Performing check for possible rootkit strings
[19:41:43] Info: Using system startup paths: /etc/rc.local /etc/init.d
[19:41:43]     Checking for string 'phalanx'                 [ Not found ]
[19:41:43]     Checking for string '/dev/proc/****it'        [ Not found ]
[19:41:43]     Checking for string '****'                    [ Not found ]
[19:41:44]     Checking for string 'backdoor'                [ Not found ]
[19:41:44]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[19:41:44]     Checking for string '/usr/sbin/login'         [ Not found ]
[19:41:44]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[19:41:44]     Checking for string 'vt200'                   [ Not found ]
[19:41:44]     Checking for string '/usr/bin/xstat'          [ Not found ]
[19:41:44]     Checking for string '/bin/envpc'              [ Not found ]
[19:41:44]     Checking for string 'L4m3r0x'                 [ Not found ]
[19:41:44]     Checking for string '/lib/libext'             [ Not found ]
[19:41:44]     Checking for string '/usr/sbin/login'         [ Not found ]
[19:41:44]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[19:41:44]     Checking for string 'sendmail'                [ Not found ]
[19:41:44]     Checking for string 'cocacola'                [ Not found ]
[19:41:44]     Checking for string 'joao'                    [ Not found ]
[19:41:44]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[19:41:44]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[19:41:44]     Checking for string '/dev/sgk'                [ Not found ]
[19:41:44]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[19:41:44]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[19:41:45]     Checking for string '/dev/proc/****it'        [ Not found ]
[19:41:45]     Checking for string '/lib/.sso'               [ Not found ]
[19:41:45]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[19:41:45]     Checking for string '/dev/caca'               [ Not found ]
[19:41:45]     Checking for string '/dev/ttyoa'              [ Not found ]
[19:41:45]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[19:41:45]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[19:41:45]     Checking for string 'syg'                     [ Not found ]
[19:41:45]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[19:41:45]     Checking for string '/dev/pts/01'             [ Not found ]
[19:41:45]     Checking for string 'tw33dl3'                 [ Not found ]
[19:41:45]     Checking for string 'psniff'                  [ Not found ]
[19:41:45]     Checking for string 'uconf.inv'               [ Not found ]
[19:41:45]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[19:41:45]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[19:41:45]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:45]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[19:41:45]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[19:41:46]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:46]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:46]     Checking for string '/bin/bash'               [ Not found ]
[19:41:46]     Checking for string '/dev/xdta'               [ Not found ]
[19:41:46]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[19:41:46]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[19:41:47]     Checking for string 'in.inetd'                [ Not found ]
[19:41:47]     Checking for string '#<HIDE_.*>'              [ Not found ]
[19:41:47]     Checking for string 'bin/xchk'                [ Not found ]
[19:41:47]     Checking for string 'bin/xsf'                 [ Not found ]
[19:41:48]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[19:41:48]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[19:41:48]     Checking for string 'ttyload'                 [ Not found ]
[19:41:49]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[19:41:49]     Checking for string 'usr/bin/xfss'            [ Not found ]
[19:41:49]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[19:41:50]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[19:41:50]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[19:41:50]     Checking for string '/ssh2d'                  [ Not found ]
[19:41:50]     Checking for string '/dev/kmod'               [ Not found ]
[19:41:51]     Checking for string '/crth.o'                 [ Not found ]
[19:41:51]     Checking for string '/crtz.o'                 [ Not found ]
[19:41:51]     Checking for string '/dev/dos'                [ Not found ]
[19:41:52]     Checking for string '/lpq'                    [ Not found ]
[19:41:52]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[19:41:52]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[19:41:52]     Checking for string '/volc'                   [ Not found ]
[19:41:53]     Checking for string 'sourcemask'              [ Not found ]
[19:41:53]     Checking for string '/bin/vobiscum'           [ Not found ]
[19:41:53]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[19:41:54]     Checking for string '/usr/bin/hdparm?-t1?-X53?-p' [ Not found ]
[19:41:54]     Checking for string '/lib/.xsyslog'           [ Not found ]
[19:41:54]     Checking for string '/etc/.xsyslog'           [ Not found ]
[19:41:55]     Checking for string '/lib/.ssyslog'           [ Not found ]
[19:41:55]     Checking for string '/tmp/.sendmail'          [ Not found ]
[19:41:55]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[19:41:55]     Checking for string 't0rnkit'                 [ Not found ]
[19:41:55]     Checking for string '/dev/proc/****it'        [ Not found ]
[19:41:55]     Checking for string 'backdoor.h'              [ Not found ]
[19:41:55]     Checking for string 'backdoor_active'         [ Not found ]
[19:41:55]     Checking for string 'magic_pass_active'       [ Not found ]
[19:41:55]     Checking for string '/usr/include/gpm2.h'     [ Not found ]
[19:41:55]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:55]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:56]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:56]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[19:41:56]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[19:41:56]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[19:41:56]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[19:41:56]     Checking for string '/dev/ida/.inet'          [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[19:41:56]     Checking for string 'backconnect'             [ Not found ]
[19:41:56]     Checking for string 'magic?packet?received'   [ Not found ]
[19:41:56]   Checking for possible rootkit strings           [ None found ]
[19:41:56]
[19:41:56] Info: Starting test name 'malware'
[19:41:56] Performing malware checks
[19:41:56]
[19:41:56] Info: Test 'deleted_files' disabled at users request.
[19:41:56]
[19:41:56] Info: Starting test name 'running_procs'
[19:42:02]   Checking running processes for suspicious files [ None found ]
[19:42:02]
[19:42:02] Info: Test 'hidden_procs' disabled at users request.
[19:42:02]
[19:42:02] Info: Test 'suspscan' disabled at users request.
[19:42:02]
[19:42:02] Info: Starting test name 'other_malware'
[19:42:02]   Performing check for login backdoors
[19:42:02]     Checking for '/bin/.login'                    [ Not found ]
[19:42:02]     Checking for '/sbin/.login'                   [ Not found ]
[19:42:02]   Checking for login backdoors                    [ None found ]
[19:42:02]
[19:42:02]   Performing check for suspicious directories
[19:42:02]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[19:42:02]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[19:42:02]   Checking for suspicious directories             [ None found ]
[19:42:02]
[19:42:02]   Checking for software intrusions                [ Skipped ]
[19:42:02] Info: Check skipped - tripwire not installed
[19:42:02]
[19:42:02]   Performing check for sniffer log files
[19:42:02]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[19:42:02]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[19:42:02]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[19:42:02]   Checking for sniffer log files                  [ None found ]
[19:42:02]
[19:42:02] Info: Starting test name 'trojans'
[19:42:02] Performing trojan specific checks
[19:42:02]   Checking for enabled inetd services             [ Skipped ]
[19:42:02] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[19:42:02]
[19:42:02]   Performing check for enabled xinetd services
[19:42:02]   Checking for enabled xinetd services            [ Skipped ]
[19:42:02] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[19:42:02]   Checking for Apache backdoor                    [ Not found ]
[19:42:03]
[19:42:03] Info: Starting test name 'os_specific'
[19:42:03] Performing Linux specific checks
[19:42:03]   Checking loaded kernel modules                  [ OK ]
[19:42:03] Info: Using modules pathname of '/lib/modules/3.13.0-51-generic'
[19:42:03]   Checking kernel module names                    [ OK ]
[19:42:34]
[19:42:34] Info: Starting test name 'network'
[19:42:34] Checking the network...
[19:42:34]
[19:42:34] Performing checks on the network ports
[19:42:34] Info: Starting test name 'ports'
[19:42:34]   Performing check for backdoor ports
[19:42:35]     Checking for TCP port 1524                    [ Not found ]
[19:42:35]     Checking for TCP port 1984                    [ Not found ]
[19:42:35]     Checking for UDP port 2001                    [ Not found ]
[19:42:35]     Checking for TCP port 2006                    [ Not found ]
[19:42:35]     Checking for TCP port 2128                    [ Not found ]
[19:42:35]     Checking for TCP port 6666                    [ Not found ]
[19:42:35]     Checking for TCP port 6667                    [ Not found ]
[19:42:35]     Checking for TCP port 6668                    [ Not found ]
[19:42:35]     Checking for TCP port 6669                    [ Not found ]
[19:42:35]     Checking for TCP port 7000                    [ Not found ]
[19:42:36]     Checking for TCP port 13000                   [ Not found ]
[19:42:36]     Checking for TCP port 14856                   [ Not found ]
[19:42:36]     Checking for TCP port 25000                   [ Not found ]
[19:42:36]     Checking for TCP port 29812                   [ Not found ]
[19:42:36]     Checking for TCP port 31337                   [ Not found ]
[19:42:36]     Checking for TCP port 32982                   [ Not found ]
[19:42:36]     Checking for TCP port 33369                   [ Not found ]
[19:42:36]     Checking for TCP port 47107                   [ Not found ]
[19:42:36]     Checking for TCP port 47018                   [ Not found ]
[19:42:36]     Checking for TCP port 60922                   [ Not found ]
[19:42:36]     Checking for TCP port 62883                   [ Not found ]
[19:42:37]     Checking for TCP port 65535                   [ Not found ]
[19:42:37]   Checking for backdoor ports                     [ None found ]
[19:42:37]
[19:42:37] Info: Starting test name 'hidden_ports'
[19:42:37] Checking for hidden ports                         [ Skipped ]
[19:42:37] Info: Unable to find the 'unhide-tcp' command
[19:42:37]
[19:42:37] Performing checks on the network interfaces
[19:42:37] Info: Starting test name 'promisc'
[19:42:37]   Checking for promiscuous interfaces             [ None found ]
[19:42:37]
[19:42:37] Info: Test 'packet_cap_apps' disabled at users request.
[19:42:37]
[19:42:37] Info: Starting test name 'local_host'
[19:42:37] Checking the local host...
[19:42:37]
[19:42:37] Info: Starting test name 'startup_files'
[19:42:37] Performing system boot checks
[19:42:37]   Checking for local host name                    [ Found ]
[19:42:37]
[19:42:37] Info: Starting test name 'startup_malware'
[19:42:37]   Checking for system startup files               [ Found ]
[19:42:38]   Checking system startup files for malware       [ None found ]
[19:42:38]
[19:42:38] Info: Starting test name 'group_accounts'
[19:42:38] Performing group and account checks
[19:42:38]   Checking for passwd file                        [ Found ]
[19:42:38] Info: Found password file: /etc/passwd
[19:42:38]   Checking for root equivalent (UID 0) accounts   [ None found ]
[19:42:38] Info: Found shadow file: /etc/shadow
[19:42:38]   Checking for passwordless accounts              [ None found ]
[19:42:39]
[19:42:39] Info: Starting test name 'passwd_changes'
[19:42:39]   Checking for passwd file changes                [ Warning ]
[19:42:39] Warning: User 'postfix' has been added to the passwd file.
[19:42:39]
[19:42:39] Info: Starting test name 'group_changes'
[19:42:39]   Checking for group file changes                 [ Warning ]
[19:42:39] Warning: Group 'postfix' has been added to the group file.
[19:42:39] Warning: Group 'postdrop' has been added to the group file.
[19:42:39]   Checking root account shell history files       [ None found ]
[19:42:39]
[19:42:39] Info: Starting test name 'system_configs'
[19:42:39] Performing system configuration file checks
[19:42:39]   Checking for SSH configuration file             [ Not found ]
[19:42:39]   Checking for running syslog daemon              [ Found ]
[19:42:39] Info: Found rsyslog configuration file: /etc/rsyslog.conf
[19:42:39]   Checking for syslog configuration file          [ Found ]
[19:42:39]   Checking if syslog remote logging is allowed    [ Not allowed ]
[19:42:39]
[19:42:39] Info: Starting test name 'filesystem'
[19:42:39] Performing filesystem checks
[19:42:39] Info: SCAN_MODE_DEV set to 'THOROUGH'
[19:42:39]   Checking /dev for suspicious file types         [ Warning ]
[19:42:39] Warning: Suspicious file types found in /dev:
[19:42:39]          /dev/.udev/rules.d/root.rules: ASCII text
[19:42:39]   Checking for hidden files and directories       [ Warning ]
[19:42:39] Warning: Hidden directory found: '/etc/.java: directory '
[19:42:39] Warning: Hidden directory found: '/dev/.udev: directory '
[19:42:40] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 
[19:42:51]
[19:42:51] Info: Test 'apps' disabled at users request.
[19:42:51]
[19:42:51] System checks summary
[19:42:51] =====================
[19:42:51]
[19:42:51] File properties checks...
[19:42:51] Files checked: 136
[19:42:51] Suspect files: 1
[19:42:52]
[19:42:52] Rootkit checks...
[19:42:52] Rootkits checked : 292
[19:42:52] Possible rootkits: 0
[19:42:52]
[19:42:52] Applications checks...
[19:42:52] All checks skipped
[19:42:52]
[19:42:52] The system checks took: 2 minutes and 42 seconds
[19:42:52]
[19:42:52] Info: End date is dom may  3 19:42:52 CEST 2015

```

I need help please. Im scary for:
```
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[878], /sbin/dhclient[12064])

[19:40:28]   /usr/bin/unhide.rb                              [ Warning ]
[19:40:28] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[19:42:39] Info: Starting test name 'passwd_changes'
[19:42:39]   Checking for passwd file changes                [ Warning ]
[19:42:39] Warning: User 'postfix' has been added to the passwd file.
[19:42:39]
[19:42:39] Info: Starting test name 'group_changes'
[19:42:39]   Checking for group file changes                 [ Warning ]
[19:42:39] Warning: Group 'postfix' has been added to the group file.
[19:42:39] Warning: Group 'postdrop' has been added to the group file.
[19:42:39]   Checking /dev for suspicious file types         [ Warning ]
[19:42:39] Warning: Suspicious file types found in /dev:
[19:42:39]          /dev/.udev/rules.d/root.rules: ASCII text
[19:42:39]   Checking for hidden files and directories       [ Warning ]
[19:42:39] Warning: Hidden directory found: '/etc/.java: directory '
[19:42:39] Warning: Hidden directory found: '/dev/.udev: directory '
[19:42:40] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 



```

What this means? I need reinstall the system? They put me a packet sniffer?
What happend with me web and bank's credit card passwords?

---

### Post by Pablo_Alvaro_Moran on 2015-05-03
I answer myself:


```
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED

```

false positive
[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)


```
Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
...
[19:42:39] Warning: User 'postfix' has been added to the passwd file.
[19:42:39] Warning: Group 'postfix' has been added to the group file.
[19:42:39] Warning: Group 'postdrop' has been added to the group file.
...
Warning: Suspicious file types found in /dev:
...
Checking for hidden files and directories 
...



```[http://ubuntuforums.org/showthread.php?t=1931897](http://ubuntuforums.org/showthread.php?t=1931897)


everything seems fine but my server made
GET [http://vip163mx00.mxmail.netease.com/](http://vip163mx00.mxmail.netease.com/) and get 404


anyone know this site? i don't understand nothing

---

### Post by bapoumba on 2015-05-03
Please start a thread in the [server section]("http://ubuntuforums.org/forumdisplay.php?f=339") for that last issue.

---

