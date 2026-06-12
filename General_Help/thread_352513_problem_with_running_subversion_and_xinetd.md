---
title: "problem with running subversion and xinetd"
date: 2007-02-03
forum: General Help
---

### Post by mmistroni on 2007-02-03
hi all,
i have installed subversion on my ubuntu 6.06, and i have followed instruction here for configuring xinetd

[http://ubuntuforums.org/showthread.php?t=187888](http://ubuntuforums.org/showthread.php?t=187888)

here's my svnserve in /etc/xinetd.d/ directory

service svnserve
{
disable=no
port=3690
socket_type=stream
protocol=tcp
wait=no
user=marco
server=/usr/bin/svnserve
server_args= -i -r /home/marco/svn
}

i have update also file in /etc/services

my svn dir is /home/marco/svn and marco is the one who owns the directory

however, after restarting xinetd i cannot see svnserve process running..
by launching sudp ps auxx|svnserve there are no processes running...

anyone can give me a hint on what am i doing wrong?

thanks in advance and regards
marco

---

### Post by aysiu on 2007-02-03
I don't even know what subversion is, but I do know this is probably where your thread belongs, so I've moved it.

---

