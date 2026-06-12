---
title: "PAM (pam_mount) is invoked by sudo"
date: 2015-05-20
forum: General Help
---

### Post by shg on 2015-05-20
Hello everybody,

recently, I setup a samba-share that is mounted every login with pam_mount. Hence, my username and password are used to mount the share.

This works fine, but I noticed that if I invoke now any command with sudo and it is required to enter my password, pam_mount is invoked, too. Can anybody explain that to me? Is there any reason for that behaviour?

Example:

```

user@machine:~$ sudo ./helloworld.sh 
[sudo] password for user: 
(rdconf1.c:744): path to luserconf set to /home/user/.pam_mount.conf.xml
(pam_mount.c:365): pam_mount 2.14: entering auth stage
Hello World
(pam_mount.c:133): clean system authtok=0x7fd0459db170 (1073741824)
user@machine:~$ 

```

Thank you :-)!

---

