---
title: "Down Them All not allowed to download!!"
date: 2008-07-02
forum: General Help
---

### Post by Chetanji on 2008-07-02
Hello to all,
I am new to Ubuntu and have a no doubt simple question.
Ubuntu 8.04 on Dell M1330 laptop

When prompted to download in Firefox, the DTA window pops up and I choose any folder and it won't allow.  If I choose automatic download it shows immediatly as "no disk space."

I have tried to log on as root but it doesn't seem to work.
I went to System>Administration>Users&Groups and gave root a password.

Please forgive this  simple question.

Thanks,
Chetanji:)

---

### Post by iaculallad on 2008-07-02
You should have privilege to save on your own Desktop since its the saving area for Firefox.

Try to check your free disk space. On your terminal:

```
df -h
```

---

### Post by Chetanji on 2008-07-02
Thanks for quick reply,

Here is the result of df -h

```
ahis@localhost:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              69G  3.3G   62G   5% /
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   72K  1.8G   1% /dev
devshm                1.8G  132K  1.8G   1% /dev/shm
lrm                   1.8G   38M  1.7G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       69G  3.3G   62G   5% /home/ahis/.gvfs
ahis@localhost:~$ 

```

It looks like I need to add some of the 60 GB unused to the existing partitions.
I am new to Linux.
Please point me in the correct direction.
Thanks iaculallad,
Chetanji:)

---

### Post by iaculallad on 2008-07-02
Disk spaces looks fine. Had you tried saving your download items in your /home directory?

Could you post whatever displays using this terminal command:

```
env|grep HOME
```

and

```
grep ahis /etc/passwd
```

---

### Post by Chetanji on 2008-07-02
```
ahis@localhost:~$ env | grep HOME
HOME=/home/ahis
```
```

ahis@localhost:~$ grep ahis /etc/passwd
ahis:x:1000:1000:ahis,,,,:/home/ahis:/bin/bash
ahis@localhost:~$ 

```

Thanks, yes I tried every directory with same problem.

---

### Post by cariboo on 2008-07-03
This might be a stab in the dark but it looks like the host name of your laptop is localhost, this may lead to confusion on the part of your computer. I would suggest you change the hostname to something else. See

```
man hostname
```

Jim

---

### Post by Chetanji on 2008-07-03
Thanks for the heads up!
I had swapped the hostname and domain name.

Strangely enough, before I checked this thread, everything was working fine with the downloading. I don't know what or why, but, firefox and DTA is working fine now.

dual boot with Win XP for work and just installed Ubuntu 8.04 yesterday.
So coming up to speed.  thanks for your help.

blessings,
chetanji:popcorn:

---

