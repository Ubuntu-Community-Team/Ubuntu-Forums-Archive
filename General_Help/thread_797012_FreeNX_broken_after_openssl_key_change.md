---
title: "FreeNX broken after openssl key change"
date: 2008-05-16
forum: General Help
---

### Post by Chireru on 2008-05-16
I got FreeNX up and going a few days ago... runs great.  However, when the openssl issue came up, I checked my system and found that one of the keys is blacklisted:
```
May 16 21:56:26 osaka sshd[12252]: Accepted publickey for nx from 10.10.221.8 port 36482 ssh2
May 16 21:56:26 osaka sshd[12254]: (pam_unix) session opened for user nx by (uid=0)
May 16 21:56:30 osaka sshd[12407]: Public key ab:27:13:51:60:84:fc:53:3d:71:42:b0:e8:a8:83:b1 blacklisted (see ssh-vulnkey(1))
May 16 21:56:31 osaka sshd[12254]: (pam_unix) session closed for user nx
```

However, I can't seem to find this key....  It isn't:
- the one it plants in ~/.ssh/authorized_keys2
- /usr/NX/home/nx/.ssh/*
- /var/lib/nxserver/home/.ssh/*
- /usr/NX/etc/keys/*
- /home/*/.ssh/*

It may be the ones in /usr/NX/share/keys/* .... for some reason ssh-vulnkey doesn't check them, or doesn't identify them as keys...?

Any ideas on where this mystery key that NX uses is?  I'm using seveas freenx on feisty-server

---

### Post by Chireru on 2008-05-16
Oh, and if I move /etc/ssh/blacklist.* out of the way and restart SSH, those errors go away (I assume the bad key is still in use) however, FreeNX still doesn't work:

```
NX> 203 NXSSH running with pid: 6112
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.10.221.4 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: tyler
NX> 102 Password: 
NX> 103 Welcome to: osaka.local user: tyler
NX> 105 listsession --user="tyler" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'tyler' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: tyler
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="256M" --media="0" --session="Osaka" --type="unix-gnome" --geometry="1024x742" --kbtype="pc102/us" --screeninfo="1024x742x24+render" 

Permission denied (publickey,password).
NX> 280 Exiting on signal: 15
```

The user in question can SSH into the machine without a problem using keys or passwords.

It appears to only be happening to one user.

Deleting that user's home directory, removing/re-adding them to NX (nxserver --userdel/--useradd) and it still doesn't work.

Tried using PAM and NX's user and password databases.

---

### Post by Chireru on 2008-05-17
After messing around with it for most of the night, I gave up and followed the how-to here, which replaced the NX software and solved the problem:
[http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976)

---

### Post by Rizla on 2008-05-20
That link didnt work for me, it didnt seem like it was going to the right post about the topic.

I'm still having this issue, if anyone has resolved the SSL issue with freenx since the update it would be greatly apprecaited.  Thanks.

---

### Post by Chireru on 2008-05-20
Weird...  I don't even remember reading that thread... :confused:

Here is the correct link; Post 2:
[http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976)

---

