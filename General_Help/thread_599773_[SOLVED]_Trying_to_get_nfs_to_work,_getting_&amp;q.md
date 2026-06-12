---
title: "[SOLVED] Trying to get nfs to work, getting &amp;quot;permission denied&amp;quot;"
date: 2007-11-01
forum: General Help
---

### Post by TeeAhr1 on 2007-11-01
I'm really just trying to learn this in case I ever actually need it in the future, but I've hit a stumbling block.  I want to share a folder called /home/me/sourcefiles-etc from a computer named no2pencil to a computer named lazarus-1.  Here's my configuration:
```
teeahr1@no2pencil:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/teeahr1/sourcefiles-etc/ lazarus-1(rw,sync,all_squash)
```
```
teeahr1@no2pencil:~$ cat /etc/default/portmap
# Portmap configuration file
#
# Note: if you manually edit this configuration file,
# portmap configuration scripts will avoid modifying it
# (for example, by running 'dpkg-reconfigure portmap').

# If you want portmap to listen only to the loopback
# interface, uncomment the following line (it will be
# uncommented automatically if you configure this
# through debconf).
#OPTIONS="-i 127.0.0.1"
```
```
teeahr1@no2pencil:~$ cat /etc/hosts
192.168.0.1     localhost
192.168.0.3     no2pencil
192.168.0.9     lazarus-1
```
So far so good, right?  Here's the rub:
```
teeahr1@lazarus-1:~$ sudo mount no2pencil:/home/teeahr1/sourcefiles-etc /media/test
mount.nfs: no2pencil:/home/teeahr1/sourcefiles-etc failed, reason given by server: Permission Denied
```
I get this in no2pencil's syslog:
```
11/01/2007 03:32:37 PM	no2pencil	mountd[5451]	mount request from unknown host 192.168.0.9 for /home/sourcefiles-etc (/home/sourcefiles-etc)
```
/etc/hosts is identical on the client machine, fwiw.  Also, I have tried editing both /etc/exports and the mount command with IP address instead of hostname, and get the same thing.  I am missing something obvious here, I can feel it.  What is it?

---

### Post by Jose Catre-Vandis on 2007-11-01
You have run
```
sudo exportfs -a
```
then ```
sudo /etc/init.d/nfs-kernel-server restart
```
on no2pencil, yes?

You also appear to have an extra / in this line in your exports file
```
/home/teeahr1/sourcefiles-etc/
``` which is not used in your mount command

---

### Post by TeeAhr1 on 2007-11-01
Thanks for the reply, I hadn't done that.  Unfortunately, I'm still getting Permission Denied...  Here's what I get in the log when I run nfs-kernel-server restart:

```
11/01/2007 07:40:00 PM	no2pencil	mountd[21128]	Caught signal 15, un-registering and exiting.

11/01/2007 07:40:01 PM	no2pencil	kernel	[90414.471968] nfsd: last server has exited

11/01/2007 07:40:01 PM	no2pencil	kernel	[90414.471974] nfsd: unexporting all filesystems

11/01/2007 07:40:01 PM	no2pencil	kernel	[90414.473709] RPC: failed to contact local rpcbind server (errno 5).

11/01/2007 07:40:02 PM	no2pencil	kernel	[90415.966087] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory

11/01/2007 07:40:02 PM	no2pencil	kernel	[90415.976102] NFSD: starting 90-second grace period
```

EDIT: It works now, but I don't know why.  I found [a href="http://www.docunext.com/category/nfs/"]this[/a] when I searched for the log message about rpcbind, so I ran the mount command as follows: "sudo mount -t nfs -o nolock no2pencil... *snip*"  Looking at man mount, -t is self-explanatory, but it has this to say about nolock: "Do not use locking. Do not start lockd."  What's that mean, and why did it work?  Also, I noticed I can't write to the directory from the client, even though it's set to rw.  Related?

---

### Post by TeeAhr1 on 2007-11-02
*bump*

---

### Post by Jose Catre-Vandis on 2007-11-02
You have hit a user permissions problem. ensure your "client user" exists on your server?

---

### Post by TeeAhr1 on 2007-11-02
Well, they're both named "teeahr1" and both have UIDs of 1000.  Do I need to do something special to let the server know it's not a local user?

---

### Post by TeeAhr1 on 2007-11-03
Oh, that was silly of me.  Even though they're the same name and UID, I still need to set the folder permissions to allow others to write.  Mark it SOLVED.  Thanks for nudging me in the right direction, Jose!

cheers-
Pete

---

