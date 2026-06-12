---
title: "Weird SSH / DNS Issue"
date: 2006-11-20
forum: General Help
---

### Post by aparsons on 2006-11-20
[U]I am having a weird ssh problem.  When I am root, I am able to ssh to a remote host: aphbgfs01.allanparsons.com.  However, when i am a regular user, it resolves aphbgfs01.allanparsons.com to a totaly different IP address.  I've never seen anything like it.

> 
root@apkcfs1:~# su - rsync
rsync@apkcfs1:~$ ssh -p 2222 -v aphbgfs01.allanparsons.com
OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to aphbgfs01.allanparsons.com [208.67.219.40] port 2222.
debug1: connect to address 208.67.219.40 port 2222: Connection refused
ssh: connect to host aphbgfs01.allanparsons.com port 2222: Connection refused
rsync@apkcfs1:~$

root@apkcfs1:/home/rsync# ssh -v -p 2222 aphbgfs01.allanparsons.com
OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to aphbgfs01.allanparsons.com [68.82.154.241] port 2222.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
[IT CONNECTS!!!!]

MY HOSTS FILE:
root@apkcfs1:/home/rsync# head -25 /etc/hosts
127.0.0.1       localhost
192.168.1.3     apkcfs1.allanparsons.com  apkcfs1
192.168.1.2     server1
192.168.1.201   hydrogen
192.168.1.110   mythtv
#192.168.1.4     aphbgfs01
#68.82.154.241  aphbgfs01.allanparsons.com


MY RESOLV.CONF FILE:
root@apkcfs1:/home/rsync# cat /etc/resolv.conf
#OpenDNS
#nameserver 208.67.222.222
#nameserver 208.67.220.220
#Univ of Pitt
nameserver 136.142.57.10
nameserver 136.142.188.73
nameserver 136.142.188.76

Also, sshd is running on the ssh server.  I dont understand why it would work fine as the root user, but not fine as a normal system user...



---

### Post by pandu.rs on 2006-11-20
can u paste the output of 
"dig aphbgfs01.allanparsons.com"
as both root user and user rsync?

---

### Post by aparsons on 2006-11-20
It seems that opendns requires you to register your IPs with them (my dns servers are pointing to opendns).  I've since done this, sat for a good 10 hours, and it works!  The problem is that my IPs are static and OpenDNS doesn't have a tool yet to dynamically update their database.

---

