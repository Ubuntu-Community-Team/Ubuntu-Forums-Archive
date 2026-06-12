---
title: "Problem creating chrooted environment"
date: 2016-02-29
forum: General Help
---

### Post by peter1897 on 2016-02-29
I am trying to create chroot environment on Ubuntu server 14.04. This is the chroot user and group i created:

```
max@ubuntu:~$ cat /etc/passwd | grep demo
demo:x:1002:1003:,,,:/home/demo:/usr/sbin/nologin
```

```
max@ubuntu:~$ cat /etc/group | grep sftpusers
sftpusers:x:1002:demo
```

This is the sshd_config file:
```
max@ubuntu:~$ tail /etc/ssh/sshd_config
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

Subsystem sftp internal-sftp

Match Group sftpusers
        ChrootDirectory /sftp/demo
        ForceCommand internal-sftp
```

This is the permissions for the chroot directory 'demo':
```
max@ubuntu:~$ ll /sftp/
total 12
drwxrwxr-x  3 root root      4096 Feb 29 18:06 ./
drwxr-xr-x 22 root root      4096 Feb 15 17:21 ../
drwxrwxr-x  2 root sftpusers 4096 Feb 15 17:22 demo/
```


But i am not able to login with the user 'demo' through sftp:
```
$ sftp demo@192.168.56.105
demo@192.168.56.105's password:
Connection reset by 192.168.56.105
Connection closed
```


Any idea it doesn't allow me to login?

---

### Post by peter1897 on 2016-02-29
I found what was the problem. The chroot directory must be owned by user root and group root and have permission 755.

---

