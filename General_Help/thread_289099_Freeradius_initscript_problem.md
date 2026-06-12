---
title: "Freeradius initscript problem"
date: 2006-10-30
forum: General Help
---

### Post by henla464 on 2006-10-30
Hello!

After upgrade to Edgy freeradius stopped working. Trying to start freeradius manually with:
```
sudo /etc/init.d/freeradius start
```
I get this error:
```
/etc/init.d/freeradius: 15: source: not found
```

So something seems to be wrong at line 15? 
Line 15 is:
```
source /lib/lsb/init-functions
```

I have a file called init-functions in /lib/lsb/

What could be wrong? All suggestions appreciated.


/Henrik Larsson

ps. I cant even uninstall freeradius because of this error. I have tried with apt-get -f remove freeradius and dpkg --remove freeradius as well as synaptic. ds.

---

### Post by MyAnda on 2006-10-30
may not be of much help, but i will through something in anyway...
you could try running the script with more output from bash to see exactly where the problem is (a function in the init-functions may be acting up)
try "bash -x /etc/init.d/freeradius start" and see what you get...if nothing jumps out at you post the results...
what is the error when you try removing freeradius?

---

### Post by henla464 on 2006-10-30
```
bash -x /etc/init.d/freeradius start
```

gives:
```
+ set -e
+ source /lib/lsb/init-functions
++ '[' -e /etc/lsb-base-logging.sh ']'
++ . /etc/lsb-base-logging.sh
+ PROG=freeradius
+ PROGRAM=/usr/sbin/freeradius
+ PIDFILE=/var/run/freeradius/freeradius.pid
+ DESCR='FreeRADIUS daemon'
+ test -f /usr/sbin/freeradius
+ '[' '!' -d /var/run/freeradius ']'
+ ret=0
+ case "$1" in
+ log_daemon_msg 'Starting FreeRADIUS daemon' freeradius
+ '[' -z 'Starting FreeRADIUS daemon' ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ usplash_write 'TEXT Starting FreeRADIUS daemon freeradius'
open: Permission denied
+ log_to_console log_daemon_msg 'Starting FreeRADIUS daemon' freeradius
+ '[' n '!=' y ']'
+ '[' no '!=' yes ']'
++ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ '[' /dev/pts/0 '!=' /dev/pts/0 ']'
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ '[' xxterm '!=' xdumb ']'
+ '[' -x /usr/bin/tput ']'
+ '[' -x /usr/bin/expr ']'
+ /usr/bin/tput hpa 60
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
++ /usr/bin/tput cols
+ COLS=80
+ '[' 80 ']'
++ /usr/bin/expr 80 - 7
+ COL=73
+ printf ' * Starting FreeRADIUS daemon freeradius       '
 * Starting FreeRADIUS daemon freeradius       ++ /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
                                                                               + printf ' '
 + start-stop-daemon --start --quiet --pidfile /var/run/freeradius/freeradius.pid --exec /usr/sbin/freeradius
Mon Oct 30 22:41:34 2006 : Info: Starting - reading configuration files ...
Mon Oct 30 22:41:34 2006 : Error: Unable to open file "/etc/freeradius/radiusd.conf": Permission denied
Mon Oct 30 22:41:34 2006 : Error: Errors reading radiusd.conf
+ log_end_msg 0
+ '[' -z 0 ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ '[' 0 -eq 0 ']'
+ usplash_write 'SUCCESS ok'
open: Permission denied
+ log_to_console log_end_msg 0
+ '[' n '!=' y ']'
+ '[' no '!=' yes ']'
++ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ '[' /dev/pts/0 '!=' /dev/pts/0 ']'
+ return 0
+ '[' 73 ']'
+ '[' -x /usr/bin/tput ']'
+ printf '\r'
+ /usr/bin/tput hpa 73
                                                                         + '[' 0 -eq 0 ']'
+ echo '[ ok ]'
[ ok ]
+ return 0
+ exit 0

```



```
sudo bash -x /etc/init.d/freeradius start
```

gave:
```
+ set -e
+ source /lib/lsb/init-functions
++ '[' -e /etc/lsb-base-logging.sh ']'
++ . /etc/lsb-base-logging.sh
+ PROG=freeradius
+ PROGRAM=/usr/sbin/freeradius
+ PIDFILE=/var/run/freeradius/freeradius.pid
+ DESCR='FreeRADIUS daemon'
+ test -f /usr/sbin/freeradius
+ '[' '!' -d /var/run/freeradius ']'
+ ret=0
+ case "$1" in
+ log_daemon_msg 'Starting FreeRADIUS daemon' freeradius
+ '[' -z 'Starting FreeRADIUS daemon' ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ usplash_write 'TEXT Starting FreeRADIUS daemon freeradius'
+ log_to_console log_daemon_msg 'Starting FreeRADIUS daemon' freeradius
+ '[' n '!=' y ']'
+ '[' no '!=' yes ']'
++ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ '[' /dev/pts/0 '!=' /dev/pts/0 ']'
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ '[' xxterm '!=' xdumb ']'
+ '[' -x /usr/bin/tput ']'
+ '[' -x /usr/bin/expr ']'
+ /usr/bin/tput hpa 60
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
++ /usr/bin/tput cols
+ COLS=80
+ '[' 80 ']'
++ /usr/bin/expr 80 - 7
+ COL=73
+ printf ' * Starting FreeRADIUS daemon freeradius       '
 * Starting FreeRADIUS daemon freeradius       ++ /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
                                                                               + printf ' '
 + start-stop-daemon --start --quiet --pidfile /var/run/freeradius/freeradius.pid --exec /usr/sbin/freeradius
Mon Oct 30 22:42:39 2006 : Info: Starting - reading configuration files ...
+ ret=0
+ log_end_msg 0
+ '[' -z 0 ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ '[' 0 -eq 0 ']'
+ usplash_write 'SUCCESS ok'
+ log_to_console log_end_msg 0
+ '[' n '!=' y ']'
+ '[' no '!=' yes ']'
++ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ '[' /dev/pts/0 '!=' /dev/pts/0 ']'
+ return 0
+ '[' 73 ']'
+ '[' -x /usr/bin/tput ']'
+ printf '\r'
+ /usr/bin/tput hpa 73
                                                                         + '[' 0 -eq 0 ']'
+ echo '[ ok ]'
[ ok ]
+ return 0
+ exit 0

```

```
 sudo apt-get remove freeradius
```
gives:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freeradius-mysql freeradius
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  freeradius freeradius-mysql
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4252kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140487 files and directories currently installed.)
Removing freeradius-mysql ...
Removing freeradius ...
/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "stop" failed.
dpkg: error processing freeradius (--remove):
 subprocess pre-removal script returned error exit status 127
/etc/init.d/freeradius: 15: source: not found
invoke-rc.d: initscript freeradius, action "start" failed.
Errors were encountered while processing:
 freeradius
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

/ Henrik Larsson

---

### Post by henla464 on 2006-10-30
When running:
```
sudo bash -x /etc/init.d/freeradius start
```

This is written to /var/log/freeradius/radius.log

```

Mon Oct 30 23:05:01 2006 : Info: Using deprecated naslist file.  Support for this will go away soon.
Mon Oct 30 23:05:01 2006 : Info: rlm_exec: Wait=yes but no output defined. Did you mean output=none?
Mon Oct 30 23:05:01 2006 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Mon Oct 30 23:05:01 2006 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Mon Oct 30 23:05:01 2006 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Mon Oct 30 23:05:01 2006 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Mon Oct 30 23:05:01 2006 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Mon Oct 30 23:05:01 2006 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Mon Oct 30 23:05:01 2006 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Mon Oct 30 23:05:01 2006 : Error: Failed creating PID file /var/run/freeradius/freeradius.pid: Permission denied 
```

---

### Post by MyAnda on 2006-10-30
just saw you posted...scratch this stuff...looks like you are on track with a perms problem

yeah sorry did not include the sudo...let me first say i have never used freeradius so I am just making guesses here...possible things to try:

walk through the start section of the freeradius init ..see what functions are being used verify that they are actually in the init-functions script and look reasonable (e.g. the files they look for are there etc.)

nasty hack - could add "exit 0" to the begining start section so that the uninstall thinks it worked...this could be bad or have no effect, i dont know  what the uninstall needs the inint to do/setup for it

backup your current init-functions, diff it with one from the last release (6.06 one attached) try starting freeradius with the old one in place and see if you get same issue 

hope it is of any help

---

### Post by henla464 on 2006-10-30
Changing the permission on the /var/run/freeradius/ helped.


Thank you MyAnda, without your help I wouldnt have solved this...

---

### Post by MyAnda on 2006-10-30
no problem, i wish i could take any credit for it :)

---

### Post by henla464 on 2006-11-01
Seems like there was still a small problem. Today I saw that freeradius wasn't started so I tried starting it. It turned out that while
```
sudo bash -x /etc/init.d/freeradius start
```
works fine (freeradius starts and works correctly), using
```
 sudo /etc/init.d/freeradius start
```
still gives
```
/etc/init.d/freeradius: 15: source: not found
```

This led me to make a small change in the /etc/init.d/freeradius script. I replaced the first line
```
#!/bin/sh
```
with 
```
#!/bin/bash
```

Now "sudo /etc/init.d/freeradius start" works!

---

### Post by chi_n_z on 2006-11-02
I replaced the first line
```
#!/bin/sh
```
with 
```
#!/bin/bash
```


Thanx this also worked for me!

---

### Post by Rich1979 on 2007-04-11
Further to this issue.  I had the same issue and it was resolved by executing:

chmod g+w /var/run/freerad

So it looks like the packagers foobar'd here....

Rich...

---

### Post by zivleyes on 2007-12-11
> **chi_n_z said:**
> I replaced the first line
```
#!/bin/sh
```
with 
```
#!/bin/bash
```


Thanx this also worked for me!

Just my two cents, there are a lot of scripts that invoke /bin/sh, this is an simple and basic old shell nowadays replaced by /bin/dash which is soflinked to /bin/sh. While sh won't run every thing that needs bash, I didn't have any problems with bash running any sh script, so I'd recommend doing the following:
```

ln -sf /bin/bash /bin/sh

```
This will avoid future problems with  "*!#/bin/sh*" scripts

---

