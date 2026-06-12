---
title: "Slow Transfer rate from ubuntu server to network pc"
date: 2016-01-05
forum: General Help
---

### Post by kahindothindot on 2016-01-05
Hi All,

I am new ubuntu user, my problem still unsolved for 2 days.
am using **Ubuntu server 14** as storage server or NAS / SAN,
when i copying 35MB file from the storage server to my PC
it is take 12min to copy.

All my Computers connected on the same HUB.

I already checked forums and put something in my samba config

and my problem still exist.
I need is to make the file transfer is fast.

i'm using NTFS on my hard disk mounted on storage server.

here's my samba config and fstab config:
Sory for my bad english. ^_^

[B]samba config:
[/B][global]


workgroup = myhome
security = ads
realm = myhome.local
domain master = no
local master = no
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
idmap backend = tdb
idmap uid = 10000-99999
idmap gid = 10000-99999
winbind enum users = yes
winbind enum groups = yes
winbind use default domain =yes
winbind nested groups = yes

[B]fstab config:

[/B]/dev/fd0    /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=54FCA39AFCA374C0 /media/storage1 ntfs uid=1000,gid=1000,umask000,sync,auto,rw,nouser 0 0

---

### Post by HermanAB on 2016-01-06
Hmm, it is probably waiting and timing out on something.  Run tcpdump and look at the packets to see what is going on.

Also run ifconfig and see whether the interface is counting any errors.  You may have a bad cable.

---

### Post by kahindothindot on 2016-01-08
Hi HermanAB,

Thank for your reply, now my network / system are running smooth.

Again thanks for your time. ^_^

---

