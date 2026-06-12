---
title: "Couple of questions about sharing with Samba!"
date: 2017-01-10
forum: General Help
---

### Post by kenshin9786 on 2017-01-10
Hi guys, really noob questions here. Don't even know if I am posting them on the right place. But here they are!

Can I have multiple "instances" of Samba running on the same machine?
How can I know if I do have this?
Could someone do this by mistake?
I was fiddling with it, configured, not sure if installed or not, purged it, installed again...
Then configured again. I could share some directories, everything was OK, but I tried to stop samba with
```
service samba stop
```
and I expected to close all sharing services or so, but my Windows machine still could access the directories, create files inside, everything.

Is this normal?

If it is, what would be the easiest way to stop sharing something, to say, temporarily, on Ubuntu? Being able to share it easily again?

By the way I am using Ubuntu 14.04.3 with XFCE, and Windows 7 SP1

Thank you in advance for any help or explanation!

---

### Post by TheFu on 2017-01-10
It is unlikely that you have multiple installs running. It isn't something that accidentally happens.

To understand the internals of the samba architecture:
 [https://www.samba.org/samba/docs/man/Samba-Developers-Guide/architecture.html](https://www.samba.org/samba/docs/man/Samba-Developers-Guide/architecture.html)

I think each client gets their own process. Until the connection times out, it will run.
Yep,
 > smbd handles all connection requests. It spawns a new process for each client connection made. That is why you may see so many of them, one per client connection.

The "service" being started/stopped is just a controller for new connections.

---

### Post by Morbius1 on 2017-01-10
> Then configured again. I could share some directories, everything was OK, but I tried to stop samba with
```
service samba stop 


```and I expected to close all sharing services or so, but my Windows  machine still could access the directories, create files inside,  everything.

Running that command should have resulted in an error message.

There is a strange interaction between the Debian SysV "samba" service and the way Upstart uses the "samba" operator.

You can find the status of "samba":
> morbius@vxub1404:~$ sudo service samba status
nmbd start/running, process 3111
smbd start/running, process 3121
But you cannot stop it:
> morbius@vxub1404:~$ sudo service samba stop
stop: Unknown instance: 
You will have to stop it's componenet parts:
> morbius@vxub1404:~$ [COLOR=#0000cd]**sudo service smbd stop**[/COLOR]
smbd stop/waiting
And do the same for nmbd.

---

### Post by kenshin9786 on 2017-01-16
Just stopping smbd as you said does the job! Thanks!


But how come I have a different behaviour now, after uninstalling Samba and installing again?


I don't know what version I had before, but running this, I get:

```
sudo smbstatus
Samba version 4.3.11-Ubuntu
```

When I started trying to share, "sudo restart service samba" resulted in the error message you mentioned: Unknow instance.


After reinstalling Samba, running that command just doesn't get any  message. Does that still means that nothing was performed or, as TheFu  says, just new connections will not be made?


Shouldn't it change its behaviour if I made some changes to Upstart, SysV or so?


I will try to run "sudo service samba stop" and then try to connect to  the shared directory from another machine, that I think will be virtual  because I only have two real ones xD


or from my phone if that is easier.

---

