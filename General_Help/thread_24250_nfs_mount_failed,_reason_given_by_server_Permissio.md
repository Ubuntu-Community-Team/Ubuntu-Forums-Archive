---
title: "nfs mount failed, reason given by server: Permission denied"
date: 2005-04-06
forum: General Help
---

### Post by ming0 on 2005-04-06
I have had this nfs server work before, but at some point, I tried to change something--and it all went to hell #-o

Client is Hoary, server is warty. When I try I get:
 ```
dean@dim:~$ sudo mount /mnt/net/
mount: 192.168.0.102:/home/net failed, reason given by server: Permission denied
``` 
The server config looks like this:
 ```
server:/home/net# cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#			   to NFS clients.  See exports(5).

/home/net dean,dana,lappy(rw,sync)
``` 
 ```
server:/home/net# cat /etc/default/portmap
# By default, listen only on the loopback interface
``` 
 ```
server:/home/net# cat /etc/hosts
127.0.0.1 localhost.localdomain localhost server
192.168.0.103 dean
192.168.0.100 dana
```
 ```
server:/home/net# sudo cat /etc/hosts.allow
All: 192.168.0.0/255.255.255.0
``` 
 ```
server:/home/net# sudo cat /etc/hosts.deny
``` 

I have purposefully disabled all the security, to make sure that isn't the problem. Anyone see any errors?

I've also reset all my services, and have followed the [nfs wiki server howto.]("http://www.ubuntulinux.org/wiki/NFSServerHowTo/view?searchterm=nfs")

---

### Post by p!=f on 2005-04-06
What server's log says?
Did you check local permissions?
Do you run user or kernel nfs server?

---

### Post by ming0 on 2005-04-06
Okay, that's a good idea--I was looking in my auth.log, instead of my syslog, last night when I posted.

I get the following error in my syslog:
 ```
Apr  6 12:19:03 localhost rpc.mountd: refused mount request from dean for /home/net (/): no export entry
``` 
So I put an IP instead, and now I can mount it. 

Now I remember the reason I started mucking around w/ my nfs server. 

[b]Whenever I try to copy anything into the mounted nfs folder (w/ nautilus or from cli, as root, or regular user), I get a strange error, and all that is made is a 0 byte file w/ the name of whatever I was copying.
[/b]
Here's an example:
 ```
dean@dim:~/Desktop$ sudo mv ./In-front-of-our-house.jpg /mnt/net/
mv: closing `/mnt/net/In-front-of-our-house.jpg': Invalid argument
dean@dim:~/Desktop$ ls -l /mnt/net/
total 175736
drwxr-xr-x  2 dean   dean		  736 2005-03-12 18:07 Fatboy Slim - Palookaville
-rw-r--r--  1 nobody nogroup		 0 2005-04-06 12:27 In-front-of-our-house.jpg
-rw-r--r--  1 dean   dean		    0 2005-04-06 12:25 KMFDM - Mortal Kombat Theme.mp3
-rwxr-xr-x  1 dean   dean	179776788 2005-03-12 18:08 Naruto 120.avi
drwxr-xr-x  2 dean   dean		  176 2005-03-12 18:08 Week 4
drwxr-xr-x  2 dean   dean		  144 2005-03-12 18:08 Week 5
-rw-r--r-- 1 dean dean		 0 2005-04-06 12:23 zach de la rocha - land and liberty.mp3
```
I'm using the kernel-server version (just like the howto wikipage recommends). I had tried a LOT of different things before, and really don't understand what's going on here. When I look on the server itself, all the 0 byte files really exist, but if I have permission to make a 0 byte file, why can't I make something else?

The other odd thing is that this doesn't add any errors to my syslog.

This is after my reset of nfs, and copying files:
 ```
Apr  6 12:22:43 localhost rpc.mountd: Caught signal 15, un-registering and exiting.
Apr  6 12:22:43 localhost kernel: nfsd: last server has exited
Apr  6 12:22:43 localhost kernel: nfsd: unexporting all filesystems
Apr  6 12:22:54 localhost rpc.mountd: authenticated mount request from dean:810 for /home/net (/home/net)
```

---

