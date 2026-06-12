---
title: "SSHFS mount in FSTAB"
date: 2021-05-14
forum: General Help
---

### Post by doubletop12 on 2021-05-14
I've just rebuilt a server from scratch and am now trying to connect to it on startup of a client. This worked before but now it doesn't. I get a ```
read: Connection reset by peer
``` message when i try to mount the updated fstab using ```
sudo mount -a
```

I can Putty to the server, ```
ssh pete@ww.xx.yy.zz
``` works as does ```
sshfs pete@ww.xx.yy.zz:/mnt/Backup /home/pete/Net_Backup
```.

I have updated my ca certs ```
sudo update-ca-certificates --fresh
``` and recreated my .ssh keys with ```
ssh-keygen
```. (Nothing worked until I did the ca certs refresh)

My fstab entry, that worked previously and now doesn't

```

pete@ww.xx.yy.zz:/mnt/Backup /home/pete/Net_Backup  fuse.sshfs _netdev,users,idmap=user,IdentityFile=/home/pete/.ssh/id_rsa,allow_other,reconnect,uid=1000,gid=1000 0 0

```

Any clues where to look next please?

Pete

---

### Post by scorp123 on 2021-05-14
> **doubletop12 said:**
>  I have updated my ca certs ```
sudo update-ca-certificates --fresh
``` (Nothing worked until I did the ca certs refresh)


The other problems aside ... I don't see the relationship between CA certificates and associated packages and SSH!?

---

### Post by scorp123 on 2021-05-14
> **doubletop12 said:**
>  I get a ```
read: Connection reset by peer
``` message when i try to mount the updated fstab using ```
sudo mount -a
```

Does "**sudo journalctl -xe**" show more information?

---

### Post by doubletop12 on 2021-05-14
Rgarding the ca-certs it seemed to fixed the problem with accessing the new build server. I just assumed that it did something to let the new server and client to share keys?

Thanks for the tip "**sudo journalctl -xe" **that threw up the error **"pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or**" an investigation into that found

[URL="https://askubuntu.com/questions/1239503/ubuntu-20-04-and-20-10-etc-securetty-no-such-file-or-directory"]https://askubuntu.com/questions/1239503/ubuntu-20-04-and-20-10-etc-securetty-no-such-file-or-directory

[/URL]Maybe not the correct solution but I fixed that by

```
sudo cp /snap/core/current/etc/securetty /etc/securetty
```


It didn't fix the problem but now the log shows multiple entries of 


> -- The job identifier is 1912.
May 15 10:59:44 eng-1 gnome-software[2476]: **not handling error failed for action get-updates-historical: failed to build result for *<long string of what could be a key?>***
May 15 10:59:44 eng-1 PackageKit[1640]: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
May 15 10:59:46 eng-1 pkexec[2539]: **pete: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/pete] [COMMAND=/usr/lib/update-notifier/>**
May 15 10:59:46 eng-1 update-notifier.desktop[2539]: **Error executing command as another user: Not authorized**
May 15 10:59:46 eng-1 update-notifier.desktop[2539]: **This incident has been reported.**
May 15 10:59:56 eng-1 polkitd(authority=local)[1110]: Operator of unix-session:c2 successfully authenticated as unix-user:pete to gain ONE-SHOT authorization for action org.fr>
May 15 10:59:56 eng-1 PackageKit[1640]: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
May 15 10:59:59 eng-1 PackageKit[1640]: refresh-cache transaction /6409_aaeabbad from uid 1000 finished with failed after 2605ms
May 15 10:59:59 eng-1 gnome-software[2476]: **not handling error download-failed for action refresh: W: GPG error: [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release: The follo>**
                                            **E: The repository 'http://dl.google.com/linux/earth/deb stable Release' is not signed.**
May 15 10:59:59 eng-1 gnome-software[2476]: **Only 0 apps for recent list, hiding**
May 15 11:00:06 eng-1 sudo[3173]:     pete : TTY=pts/0 ; PWD=/home/pete ; USER=root ; COMMAND=/bin/journalctl -xe
May 15 11:00:06 eng-1 sudo[3173]: pam_unix(sudo:session): session opened for user root by (uid=0)


However one other problem I have been getting when I rdp/xorg into the clients I'm having the problem with is regular popups requesting authoristation and entering a password.

Pete

---

### Post by doubletop12 on 2021-05-14
Thanks for the input, it got me thinking a bit more and investigating the logs. I then found this old post. I'm sure I searched for something similar but hadn't found this

[URL="https://askubuntu.com/questions/314444/sshfs-with-fstab-connection-reset-by-peer"]https://askubuntu.com/questions/314444/sshfs-with-fstab-connection-reset-by-peer

[/URL]So included "debug" in the sshfs line in fstab

```
pete@ww.xx.yy.zz:/mnt/Backup /home/pete/Net_Backup  fuse.sshfs _netdev,users,**debug**,idmap=user,IdentityFile=/home/pete/.ssh/id_rsa,allow_other,reconnect,uid=1000,gid=1000 0 0
```

Then unmounted the link and remounted

 
> pete@zzzz:/media$ sudo umount /home/pete/Net_Backup
umount: /home/pete/Net_Backup: not mounted.
pete@zzzz:/media$ sudo mount -a
FUSE library version: 2.9.9
nullpath_ok: 0
nopath: 0
utime_omit_ok: 0
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:*<key string>*
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /root/.ssh/known_hosts:1
  remove with:
  ssh-keygen -f "/root/.ssh/known_hosts" -R "ww.xx.yy.zz"
ECDSA host key for ww.xx.yy.zz has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer

running the following fixed the keys problem
```

ssh-keygen -f "/root/.ssh/known_hosts" -R "ww.xx.yy.zz"
```

So I was on the right track just didn't know how to update the keys for the rebuilt server.

*For those that manage these things <SOLVED>*

Pete

---

### Post by TheFu on 2021-05-15
There is a "Thread Tools" button near the top.  Only the original poster can mark a thread as SOLVED.  It will save people coming to help from bothering.  Please and thank you.

---

