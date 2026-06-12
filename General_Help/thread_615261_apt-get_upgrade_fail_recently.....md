---
title: "apt-get upgrade fail recently....?"
date: 2007-11-16
forum: General Help
---

### Post by zkchong on 2007-11-16
Dear people,

I have a few security patches that failed to be upgraded recently. These are the output of the command. I have tried to use --fix-missing to fix the error but result still the same.

Can someone suggest me any solution? 
Thank you,



zkchong@zkchong-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8606kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


zkchong@zkchong-laptop:~$ sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8606kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden

---

### Post by OldSchoolNoob on 2007-11-16
My guess is that everyone has this issue right now. :( 
I tried to manually download the update and got the same issue on the website. My guess is that there was a typo and the package is in the wrong place or something stupid like that. :) But I really wouldn't worry about it.

---

### Post by FuturePilot on 2007-11-16
Yes, everyone is having this problem. The update didn't properly fix the security vulnerability so they blocked it from being downloaded.
[http://ubuntuforums.org/showthread.php?t=463944]("http://ubuntuforums.org/showthread.php?t=463944")

---

