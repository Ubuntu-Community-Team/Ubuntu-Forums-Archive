---
title: "useradd: warning: the home directory already exists."
date: 2007-03-30
forum: General Help
---

### Post by lptr on 2007-03-30
Having a weird problem:
```
# /usr/sbin/useradd -s /bin/false -d /dev/null -m testuser_a
```

results in this message:
```
useradd: warning: the home directory already exists.
Not copying any file from skel directory into it.
```

```
# ls -al
insgesamt 36
drwxrwxr-x  6 root          root           4096 2007-03-30 19:14 .
drwxr-xr-x 21 root          root           4096 2007-03-26 08:40 ..
drwxrwxr-x  3 administrator administrator  4096 2007-03-30 17:52 administrator
lrwxrwxrwx  1 root          root             44 2007-03-22 09:35 .directory -> /etc/kubuntu-default-settings/directory-home
drwxrw----  2 root          root          16384 2007-03-22 09:35 lost+found
drwxrwxr-x 34 rob           rob            4096 2007-03-30 18:26 rob
drwxrwxr-x  4 root          administrator  4096 2007-03-26 16:49 samba
```

Any ideas?

rob*

---

### Post by SishGupta on 2007-03-30
You are trying to create a home directory in /dev/null?

Why do you just not make a homedir all together...

/dev/null isnt a folder it is a device, you can output to it but i dont think you can create folders and such there...

---

### Post by lptr on 2007-03-31
> /dev/null

I'm fiddeling around for more than a day, to find out why Samba does not create a new user. I assume during the testings I sat to close to the problem :(

Of course you are right. Thank you for help.

I think now it is time to should start another thread with Samba.

rob*

---

