---
title: "nessus-update-plugins fails"
date: 2005-10-27
forum: General Help
---

### Post by rossellamj on 2005-10-27
We have installed Nessus though apt-get and we are having problems updating the plugins, I tried to update them in many ways, I tried to register too but it failed. I also noticed that Nessus is failing to update the plugins on another machine that is running Red Hat. Any idea anybody? tia, here's the specifics:

root@cccnes:/home/rmj# nessus-update-plugins
[8683] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket
Could not retrieve the plugins MD5
Aborting

root@cccnes:/home/rmj# nessus-fetch --plugins
[8686] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket

root@cccnes:/home/rmj# nessus-update-plugins -vv
+ for i in '$opts'
+ case $i in
+ '[' -z y ']'
+ tar=-xvf
+ '[' '!' -d /var/lib/nessus/plugins ']'
++ pwd
+ cwd=/home/rmj
+ tmpdir=
+ test -z ''
+ tmpdir=
+ test -z ''
+ tmpdir=/tmp
+ mkdir -m 0700 /tmp/nessus-update-plugins-8687
+ cd /tmp/nessus-update-plugins-8687
+ /usr/bin/nessus-fetch --plugins-md5
[8693] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket
+ echo 'Could not retrieve the plugins MD5'
Could not retrieve the plugins MD5
+ echo Aborting
Aborting
+ exit 1

root@cccnes:/home/rmj# nessus-fetch --register 8B77-742F-65BE-277F-83E7
[8694] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/443=1;
']: Socket operation on non-socket

---

### Post by rossellamj on 2005-10-27
I just noticed that nessus.org is not reachable either, maybe that's related to this problem.

---

### Post by Riverside on 2005-10-27
> **rossellamj][8683] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1 said:**
> : Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socketIt appears that your machine is unable to connect to [www.nessus.org](www.nessus.org) on destination TCP port 80.  Do you normally access the web via a local or external proxy listening on a different port?  Is direct outbound destination TCP port 80 traffic blocked from the machine in question, by to a firewall device?

---

### Post by Riverside on 2005-10-27
In fact:

[http://mail.nessus.org/pipermail/nessus/2005-October/msg00280.html](http://mail.nessus.org/pipermail/nessus/2005-October/msg00280.html)

Nessus are experiencing network issues and the update server cannot be reached at present.

---

