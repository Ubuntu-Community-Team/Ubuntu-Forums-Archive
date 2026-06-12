---
title: "After serious damage, unable to su - root"
date: 2008-04-30
forum: General Help
---

### Post by Questor21 on 2008-04-30
Yesterday I did the following from /

```
sudo chown -R myuser:myuser *
```

I ^C'd the command but not before it chown'd /dev /boot /bin /dev /cdrom

Using my coworker's directory lists as a template, and some scripting, I have reset my /dev /boot /bin /dev directories with what I feel is 97+% accuracy.  (pulled a number outta my ***)

However I cannot su - root

I have done:

```
sudo passwd root
```

To set it, but I'm still getting:

```
myuser@myhostname:~/tmp/tmp$ su - 
Password: 
su: Authentication failure
```

Any ideas?  For all you people out there who say, "WHY DO YOU NEED TO LOGIN AS ROOOT!!!! WTF!"  It's because the Lotus Notes 8 install is buggy when run as sudo and only when run as root does it install well.

---

### Post by jjk7288 on 2008-04-30
I'd be inclined to say that either your /etc/passwd or /etc/shadow file is owned by someone other than root. Make sure that, for shadow, owner should be root:shadow and permissions should be 640.

/etc/passwd should be owned by root:root and have permissions 644.

---

### Post by Questor21 on 2008-04-30
From auth.log

```
Apr 30 14:56:07 dst0092953lx su[10540]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 14:56:07 hostname su[10540]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 14:56:07 hostname su[10540]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 14:56:11 hostname su[10540]: pam_unix(su:auth): authentication failure; logname=user uid=1000 euid=1000 tty=pts/1 ruser=user rhost=  user=root
Apr 30 14:56:13 hostname su[10540]: pam_authenticate: Authentication failure
Apr 30 14:56:13 hostname su[10540]: FAILED su for root by user

```

---

### Post by Questor21 on 2008-04-30
```
-rw-r--r-- 1 root root   1239 2008-04-30 14:31 group
-rw-r--r-- 1 root root   1814 2008-04-30 14:31 passwd
-rw-r----- 1 root shadow 1236 2008-04-30 14:51 shadow
```

---

### Post by scorp123 on 2008-04-30
> **Questor21 said:**
> From auth.log

```
Apr 30 14:56:07 dst0092953lx su[10540]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 14:56:07 hostname su[10540]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]user

``` I think the error message is pretty clear? Why don't you check the file the error message is mentioning?

---

### Post by wirelessmonkey on 2008-04-30
I believe the proper command to su to root is: sudo su

---

