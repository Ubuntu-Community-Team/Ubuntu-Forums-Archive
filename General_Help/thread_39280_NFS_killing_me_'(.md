---
title: "NFS killing me :'("
date: 2005-06-04
forum: General Help
---

### Post by Gandalf on 2005-06-04
Hey guys,

**Problem**

i don't know why, but NFS suddenly stop working yesterday night, i wanted to unmount my shared USB HDD so i stoped manually nfs-kernel-server, and portmap, after i plug it (even after server-client restarting) i keep getting the message
```

wael@nasreddine:~$ sudo mount /media/WAEL_FAT/
mount: 192.168.3.2:/media/WAEL_FAT: can't read superblock
wael@nasreddine:~$

```


**Information**
client:

```

wael@nasreddine:~$ rpcinfo -p 192.168.3.2
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100021    1   tcp  32768  nlockmgr
    100021    3   tcp  32768  nlockmgr
    100021    4   tcp  32768  nlockmgr
    100005    1   udp    865  mountd
    100005    1   tcp    868  mountd
    100005    2   udp    865  mountd
    100005    2   tcp    868  mountd
    100005    3   udp    865  mountd
    100005    3   tcp    868  mountd
    100024    1   udp    603  status
    100024    1   tcp    606  status
wael@nasreddine:~$
wael@nasreddine:~$ ps -edf |grep po
daemon    6543     1  0 13:51 ?        00:00:00 /sbin/portmap
wael@nasreddine:~$ cat /etc/fstab
192.168.3.2:/media/WAEL_FAT     /media/WAEL_FAT nfs     rw,hard,intr,noauto     0       0
192.168.3.2:/   /media/SERVER   nfs     rw,hard,noauto  0       0
192.168.3.2:/media/REDOUANE     /media/REDOUANE nfs     rw,hard,intr,noauto     0       0


```


server:
```

server:/etc# cat /etc/exports
/       192.168.1.0/255.255.255.0(rw,sync) 192.168.2.0/255.255.255.0(rw,sync)

/media/WAEL_FAT 192.168.1.0/255.255.255.0(rw,sync) 192.168.2.0/255.255.255.0(rw,sync)

/media/REDOUANE 192.168.1.0/255.255.255.0(rw,sync) 192.168.2.0/255.255.255.0(rw,sync)
server:/etc# cat hosts.allow
portmap: 192.168.2.0/255.255.255.0 192.168.1.0/255.255.255.0
mountd: 192.168.2.0/255.255.255.0 192.168.1.0/255.255.255.0
rquotad: 192.168.2.0/255.255.255.0 192.168.1.0/255.255.255.0
statd: 192.168.2.0/255.255.255.0 192.168.1.0/255.255.255.0
server:/etc# cat hosts.deny
portmap: ALL
mountd: ALL
rquotad: ALL
statd: ALL
server:/etc# cat fstab
### adding external Hard disks
/dev/sda2       /media/WAEL_FAT vfat    defaults,auto,uid=1000,gid=1000,iocharset=utf8  0       0
server:/etc# ls /media/WAEL_FAT/
AuthorizationForm.doc  ClickHere.exe  ClickHere.ini  CRAZY FROG Axel F .wma  gdiplus.dll  mmc  Redouane_merci wael  server.zip  wael  yvon

```

**Question**
what's going on, i tried almost everything, i can't get into the HDD using NFS :o


**Thanks in advance**

---

### Post by Gandalf on 2005-06-04
ok so far i could mount it from the server itself using
mount -t nfs 127.0.0.1:/media/WAEL_FAT /mnt/temp
no errors occured...

any suggestions???

---

### Post by Gandalf on 2005-06-05
no one around????

---

