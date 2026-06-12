---
title: "Can't get Transmission-daemon to start"
date: 2012-12-14
forum: General Help
---

### Post by springs1 on 2012-12-14
Hi all,

I've just installed Ubuntu Server 12.10 onto my server as my previous install of Fedora decided to commit suicide.

I've installed and configured transmission as per my previous install on the old server but i am having issues where the program wont start..

```
sudo service transmission-daemon start
transmission-daemon start/running, process 2010
``````
 sudo service transmission-daemon status
transmission-daemon stop/waiting
```If i run the above commands it says it's started but asking the status of it, it's saying it's stopped..

Any ideas?

---

### Post by bellmr on 2013-01-12
I am having the same issue. Everything works fine if I start using

```
>sudo transmission-daemon -g /etc/transmission-daemon
```

If I don't use the -g option, then I am not able to connect from a remote machine.

---

### Post by qnub on 2013-09-06
Have same issue and found that i've been change transmission-daemon user to «samba:sambashare», but after update folder rights been changed to default «debian-transmission:debian-transmission». So check file/folders rights:

/etc/transmission-daemon/settings.json <- transmussion process user must have write rights here
/var/lib/transmission-daemon <- folder with cache, support files, etc, must be also writeable

To check current transmission-damon process user open /etc/init/transmission-daemon.conf and find «setuid»/«setgid» parameters.

Also right «-g» parameter isn't «/etc/transmission-daemon» is «/var/lib/transmission-daemon/info», you can check it in «/etc/default/transmission-daemon»

---

