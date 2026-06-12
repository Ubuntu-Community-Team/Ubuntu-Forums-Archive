---
title: "how do i access hostpc from vmware server"
date: 2006-12-20
forum: General Help
---

### Post by mmoalem on 2006-12-20
hi there all - installed vmware server on kubuntu and have winxp as guest os and all looks promising except for the fact that i dont know how to access the ubuntu and all other host pc partions. (i can access the internet from within the guest os)
any ideas?
cheers
michel

---

### Post by marcantonio on 2006-12-20
There are a few ways.  I run sshd on Ubuntu and WinSCP on the guest Windows OS.

You can also use Samba.

Marc

---

### Post by mmoalem on 2006-12-21
hi Marc and thanks for the reply but i'm afraid that as a fairly newbie i need some more details... for example i thought samba was a protocol to let the linux machine read windows network file system. I need it in reverse - the windows virtual machine to read the linux host...
i got as far as installing openssh...
also - i was under the impression that you can drag files from desktop into the virtual desktop... was i wrong? is it a windows only feature? or do i need to install another thing?
cheers
michel

---

### Post by louistan3 on 2006-12-21
i am unsure about this.. but can the guest OS see the host OS partitions? 
if so.. then maybe u jst need to install fs-driver in the guest OS and ul be able to read the partitions.. fs-driver allows windows to read ext2 partitions.. u can download it from [www.fs-driver.org](www.fs-driver.org)

hope this helps :D

---

### Post by mmoalem on 2006-12-21
well i cant see any workgroup computers or any of the host partitions (i have ext2, ntfs and fat32 partitions on 3 hard disks on host system - all mounted and working on ubuntu)
cheers
michel

---

### Post by darrenm on 2006-12-21
Sounds bad but the easiest way is to use samba-server.

install samba-server then browse to the linux box from the windows box pretending they are independent computers on the same network.

---

### Post by marcantonio on 2006-12-21
> **mmoalem said:**
> hi Marc and thanks for the reply but i'm afraid that as a fairly newbie i need some more details... for example i thought samba was a protocol to let the linux machine read windows network file system. I need it in reverse - the windows virtual machine to read the linux host...
i got as far as installing openssh...
also - i was under the impression that you can drag files from desktop into the virtual desktop... was i wrong? is it a windows only feature? or do i need to install another thing?
cheers
michel

Michel,

I don't know much about Samba but from what I understand it would work as darrenm said, the host OS and the guest OS look like Windows shares to each other (and anyone else for that matter).

As I said, I use ssh.  I believe the OpenSSH server comes with a default Ubuntu install.  If not it's:
```
sudo apt-get install openssh-server
```To start and stop:
```
sudo /etc/init.d/ssh start
sudo /etc/init.d/ssh stop
```It should already be in your start up scripts as well.  If not, and you want it there:
```
sudo ln -s /etc/init.d/ssh /etc/rc2.d/S20ssh
```I think there's a gui for that one some where.

Now on the Windows side install WinSCP from winscp.net.  It gives you a gui ftpish program that you can copy files from and to with.  I'm sure there are other clients out there as well.

That, in my opinion, is a lot easier than setting up and worrying about Samba.  But to each his own.

As far as dragging files to and from the desktop, I seem to remember reading that that is a Windows only feature.

Hope that clears things up a little.

-Marc

---

