---
title: "Properly setting ulimit"
date: 2014-05-03
forum: General Help
---

### Post by DigiAngel on 2014-05-03
Hey all,

So...I'm using logstash which is now giving me a "too many open files" error.  I know that this is a ulimit problem.  Trying to set this via command line I get:

[08:43:54 @gateway:~$] ulimit -n
1024

[08:43:57 @gateway:~$] ulimit -n 65000
-bash: ulimit: open files: cannot modify limit: Operation not permitted

[08:44:03 @gateway:~$] sudo ulimit -n 65000
sudo: ulimit: command not found

How is this really set?  I've tried to set it via reboot with adding:
user  soft  nofile 9000
user  hard  nofile 65000

to /etc/security/limits.con

and adding:

session required 	pam_limits.so

to /etc/pam.d/common-session

But still no luck....reboot and all I got is 1024.  What's the real methed to get this to work?  Thank you.

---

### Post by Doug S on 2014-05-03
Here is how I did it (/etc/security/limits.conf):```
# /etc/security/limits.conf
#
[COLOR=#ff0000]# Smythies.com specific edits. 2011.01.06[/COLOR]
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
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
[COLOR=#ff0000]#        - nofile - max number of open files (smythies.com - so Samba will not complain)
* - nofile 16384[/COLOR]
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

# End of file
```

---

### Post by DigiAngel on 2014-05-03
I'll give that a go..thanks Doug.

---

