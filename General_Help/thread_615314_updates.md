---
title: "updates?"
date: 2007-11-16
forum: General Help
---

### Post by old-codger on 2007-11-16
Being new to ubuntu, I have always installed the updates when the updater poped up. There has always been a list of changes and a discription. The updater says I have updates but  there is no list of changes. It says the list is not available to check back later. I have checked back for a week and still no list. I have since received notice of more updates and the changes list is just blank. Now my question. Does ubuntu ever do this or is this some bad software trying to be installed on my system? I have not installed anything since I can't decide if it is the real thing.  
                                          Old-Codger

---

### Post by taurus on 2007-11-16
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by old-codger on 2007-11-17
Ran the sudo update, A lot so stuff came up and at the bottom said done. Upgrade said some changes would be made and did I want to continue. Some were ones in the pop up update. I said yes. I guess it done it's magic but I still have a notification icon and it still list the same things. The icon did dim while all of this was happening. Also got several 403 forbiden reports.  I forgot in the first post that I am running dapper drake.
     Old-Codger

---

### Post by taurus on 2007-11-17
It would be nice if you can post the complete error message but I bet it has something to do with samba!

[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by amadeus266 on 2007-11-17
This is what I am getting.

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9290kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err http://security.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err http://security.ubuntu.com gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by taurus on 2007-11-17
> **amadeus266 said:**
> This is what I am getting.

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9290kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err http://security.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err http://security.ubuntu.com gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Already told you and I even provided you with the links so you can read them yourself.

Maybe you ought to read this one then.
[http://ubuntuforums.org/showpost.php?p=3786506&postcount=45](http://ubuntuforums.org/showpost.php?p=3786506&postcount=45)

---

### Post by old-codger on 2007-11-17
I don't know how to get the error message on the post but yes I saw some stuff about samba. The update has samba listed in it also. Old-codger

---

### Post by old-codger on 2007-11-17
Thanks Taurus, I read the post you suggested to amadeus266 and will wait and let them get it all sorted out. Again thanks again
                                  Old-codger

---

