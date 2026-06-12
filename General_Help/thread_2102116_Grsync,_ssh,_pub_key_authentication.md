---
title: "Grsync, ssh, pub key authentication"
date: 2013-01-06
forum: General Help
---

### Post by iowabeakster on 2013-01-06
I've been using Grsync to back up my /home to a locally connected external drive, no problems, works great.  This is on "my" desktop PC. (Xubuntu 12.04)

I want to be able to use it to back up /home, on my wife's laptop, to the same external drive via ssh over our home network. (her OS is Ubuntu 12.04)

I have ssh clients and hosts running on both machines.  I have public key authentication working in both directions (passwords disabled).  Ssh in terminal, and through Nautilus and Thunar, work perfectly in both directions.

I can't get ssh to work with Grsync.  I get: 

```
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
Rsync process exit status: 255
```

On her laptop I have the following included in "additional options" in Grsync:

```
--exlude=/home/amy/.gvfs
-e "ssh -i /home/amy/.ssh/id_rsa"
```

The Grsync destination file reads as:

kirk@192.168.0.4:/media/freeagent/amy-home-backup

Like I said, I can connect to my desktop via ssh, with key authentication, both via terminal and Nautilus.

---

### Post by iowabeakster on 2013-01-06
I figured it out.

I was using the same settings, on my wife's laptop, that I used in Grsync on my desktop PC.  I had "run as superuser" checked.  I need to do that on my desktop in order to backup multiple users.

But, I can't connect via ssh as su (I have connect as su disabled in my sshd_config).  And so it was refusing connection.  So, simply unchecking the "run as superuser" in Grsync on my wife's laptop was all I needed to do.

---

