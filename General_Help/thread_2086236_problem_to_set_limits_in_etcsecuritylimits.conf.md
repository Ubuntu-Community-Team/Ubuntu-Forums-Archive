---
title: "problem to set limits in /etc/security/limits.conf"
date: 2012-11-20
forum: General Help
---

### Post by rnerwein on 2012-11-20
hello
looks like i (or ubuntu) have a problem to set ulimits for users ( not admin user ).
here is my configuration of limits.conf:

how to set the ulimit as admin for another user.
/etc/security/limits.conf seems not working ([COLOR=Green] even after reboot[/COLOR] )
here my configuration of limits.conf
#<domain>      <type>  <item>         <value>
#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
[COLOR=Blue]test             soft    data            512000
test             hard    data            614000
test             soft    stack             8192
test             hard    stack            16384
test             soft    as              512000
test             hard    as              614000

[COLOR=Black]after login as[COLOR=Red] user tes[/COLOR]t ulimit -a gives me:
testuser@tschang:~/src/test$ ulimit -a
core file size          (blocks, -c) 0
[COLOR=Red]data seg size           (kbytes, -d) unlimited[/COLOR]
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 28962
max locked memory       (kbytes, -l) 64
[COLOR=Red]max memory size         (kbytes, -m) unlimited[/COLOR]
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192

my question is - is it my mistake or is it a bug ?????


[/COLOR][/COLOR]

---

