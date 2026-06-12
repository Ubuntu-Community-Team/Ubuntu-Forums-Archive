---
title: "windows share  Permission denied"
date: 2018-05-03
forum: General Help
---

### Post by bizhat on 2018-05-03
I am mounting a windows share on ubuntu.

```
root@ok-pc-1:~# mount -t cifs //192.168.0.48/downloads /media/downloads -o username=<username>,password=<password>,uid=<uid>,iocharset=utf8,sec=ntlm,rw,dir_mode=0777,file_mode=0666
root@ok-pc-1:~# 
root@ok-pc-1:~# ls -l /media/downloads
ls: reading directory '/media/downloads': Permission denied
total 0
root@ok-pc-1:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               976M     0  976M   0% /dev
tmpfs                              200M  5.7M  194M   3% /run
/dev/mapper/ok-pc-1--vg-root   38G  2.1G   34G   6% /
tmpfs                              996M     0  996M   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              996M     0  996M   0% /sys/fs/cgroup
/dev/sda1                          472M   58M  390M  13% /boot
tmpfs                              200M     0  200M   0% /run/user/1000
//192.168.0.48/downloads           200G  131G   70G  66% /media/downloads
root@ok-pc-1:~# ls -l /media
total 12
drwxr-xr-x 2 root     root 4096 May  3 11:42 cdrom
drwxrwxrwx 2 <uid> root    0 May  3 03:28 downloads
lrwxrwxrwx 1 root     root    7 May  3 11:42 floppy -> floppy0
drwxr-xr-x 2 root     root 4096 May  3 11:42 floppy0
drwxr-xr-x 2 root     root 4096 May  3 12:31 fmb
root@ok-pc-1:~# 

```

Any idea why i am  getting permission denied after mounting ?

---

### Post by TheFu on 2018-05-03
a) Best not to post your password on the internet.
b) Best to use a credentials=   option instead of username/password in the command.
c) uid= should have a NUMBER, not a username.
d) Depending on the Windows version, better security and performance can be had with newer versions of the protocol and ntlmv2.

If you have username, you don't need uid.

"administrator" is a less great choice for a username.   Think about using a pseudo-random username, not something expected to be standard.  

OTOH, it is your box.

---

### Post by QIII on 2018-05-03
Username, password and UID redacted.

---

### Post by bizhat on 2018-05-03
Thanks for the reply.

> **TheFu said:**
> a) Best not to post your password on the internet.

It is not actual, i just generated a random password, replace the original before posting :)

> **TheFu said:**
> 
b) Best to use a credentials=   option instead of username/password in the command.


Thanks, i am doing that now. Created credentials file.


> **TheFu said:**
> 
c) uid= should have a NUMBER, not a username.


It take both number and user name ? The user name i put is working as you can see in  "ls -l" result posted. I will use id of user instead.


> **TheFu said:**
> 
d) Depending on the Windows version, better security and performance can be had with newer versions of the protocol and ntlmv2.


I tried all available security option shown in "man 8 mount.cifs", but only sec=ntlm works. Everything else just hangs or give some error.


> **TheFu said:**
> 
"administrator" is a less great choice for a username.   Think about using a pseudo-random username, not something expected to be standard.  


Thanks, i will check it.

Still have "Permission denied" error. Not sure if its something on windows side as i don't have direct access to this windows server, doing it remotely on SSH.

---

### Post by TheFu on 2018-05-03
Windows version?  Different versions support different CIFS protocol versions, which are specified in the mount options.
Win7 and later support ntlmv2 which vastly improves security.  The cifs protocol version is specified using vers=2.0 

The username/password stuff inside the credentials= file is for Windows. Obviously, those have to exist and have share access to the source.

The uid= is the number for Unix.  I tend to use gid= instead, since I want groups of people to have access,not just 1 person.

About once every 2 months, my Win7 machines stop sharing. It is a Windows bug. Only reboot seems to fix it. I've tried about 10 "fixes" for the issue found at Windows websites.  They improved it from a weekly issue to a semi-monthly problem.

I don't have Windows-Server or AD.

The mount point needs to have permissions appropriate for the uid/gid on Unix.

That's about all I know for this stuff.  There are logs that might be helpful and I suspect there's a way to get mount with more verbosity?  --verbose.

Just checked ... I was wrong:```

       uid=arg
           sets the uid that will own all files or directories on the mounted
           filesystem when the server does not provide ownership information.
           It may be specified as either a username or a numeric uid. When not
           specified, the default is uid 0. The mount.cifs helper must be at
           version 1.10 or higher to support specifying the uid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND
           PERMISSIONS below for more information.
```
Looks like either a unix username OR a uid can be used.  That's confusing because uid is a number for every other command.

---

### Post by bizhat on 2018-05-04
Thanks for the info. The problem with the share was it was in a domain. The windows version they use is very old, Windows Server 2000.

---

### Post by TheFu on 2018-05-04
> **bizhat said:**
> Thanks for the info. The problem with the share was it was in a domain. The windows version they use is very old, Windows Server 2000.

Having any unsupported/unpatched Windows version on a network, any network, is a huge security risk.  Hard to mitigate ... actually, I'd replace that WinSrv with a Linux one. ;)

---

### Post by bizhat on 2018-05-04
I am just doing the Ubuntu server setup because they don't know Linux.  They are supposed to know Windows, but from this Windows Server 2000, i doubt it :) Setting up Linux is a good thing, they may slowly move to Linux once they find out how good it runs.

---

