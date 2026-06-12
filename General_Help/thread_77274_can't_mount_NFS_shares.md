---
title: "can't mount NFS shares"
date: 2005-10-16
forum: General Help
---

### Post by kerinin on 2005-10-16
ok, i have a laptop and a desktop, i'm going to use the desktop as a server, and i'd like the laptop to use the desktop's /home directory whenever possible.  

i opened up 'sharing' on the desktop and told it to share /home using NFS, then added 'eth0 local network' as an allowed host.  OK

i then went to the laptop and added the following line to /etc/fstab:
```
192.168.1.100:/home /home nfs proto=tcp,defaults 0 0
```
then i rebooted the labtop.  OK

laptop gives me the following error:
```
mount: RPC: Program not registered
```

to be sure, i try simply mounting the NFS share manually, same thing:
```
kerinin@euclid:~$ sudo mount newKid:/home /home
Password:
mount: RPC: Program not registered

```

help?  :(

---

### Post by drogoh on 2005-10-16
Is portmap running?

---

### Post by gdcondor on 2005-10-18
i've the same pb between two breezy and portmap is running on both (/sbin/portmap on the server and /sbin/portmap -i 127.0.0.1 on the client)

---

### Post by MemoryDump on 2005-11-17
[QUOTE=gdcondor]i've the same pb between two breezy and portmap is running on both (/sbin/portmap on the server and /sbin/portmap -i 127.0.0.1 on the client)[/QUOTE]
I was having the same prob until I did:

```
sudo apt-get install portmap
```

---

### Post by cubeice24 on 2006-04-26
I'm running Hoary and here's the list of things I did on my **server** machine in order to get a succesful mount:
1)apt-get-installed portmapper, nfs-common and nfs-kernel-server
2)edited /etc/exports : /home/ez/Shared 139.8.8.25(rw)
3)restarted the following services:
   /etc/init.d/portmap restart
   /etc/init.d/nfs-common restart
   /etc/init.d/nfs-kernel-server restart

---

### Post by marcelloconti on 2006-04-26
Hi, 
I have this problem, and now is working nice and full.

1- Install -> apt-get install portmap nfs-common

2- Run services in these order:
/etc/init.d/nfs-common restart
/etc/init.d/portmap restart

try to mount your shares.

remember, portmap is the last service to restart/start.

---

