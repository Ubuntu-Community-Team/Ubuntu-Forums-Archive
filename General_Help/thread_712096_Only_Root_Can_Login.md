---
title: "Only Root Can Login??"
date: 2008-03-01
forum: General Help
---

### Post by ericinwisconsin on 2008-03-01
Suddenly, I can only log into the GUI (KDE) as root. Not as any other user. I tried deleting and recreating a user; no luck. I tried creating a NEW user; no luck.

I tried:

/usr/bin/lsattr `echo $PATH | tr ':' ' '` | grep i--

Nothing odd, so I don't think I've been hacked. The logs show nothing out of the ordinary, although I'm not 100% positive what to look for as far as a failure to log in is concerned. I can still log in via SSH.

Any ideas/suggestions?

Eric
:confused:

---

### Post by taurus on 2008-03-01
Can you post the output of this command?

```
ls -la /home
```
When you try to log in as a regular user, do you get any error message at all?

---

### Post by ericinwisconsin on 2008-03-01
Here's the output of ls -la /home:

drwxr-xr-x  7 root      root        4096 2008-03-01 10:31 .
drwxr-xr-x 21 root      root        4096 2008-02-12 00:39 ..
lrwxrwxrwx  1 root      root          44 2007-12-15 18:58 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x 59 eric      eric     393216 2008-03-01 10:00 eric
drwxr-xr-x  2 root      nogroup     4096 2008-01-01 19:43 ftp
drwxr-xr-x 15 jake      jake        4096 2008-02-03 22:06 jake
drwxr-xr-x 15 marlene   marlene     4096 2008-03-01 10:12 marlene
drwxr-xr-x  2 test_user test_user   4096 2008-03-01 10:33 test_user

When I try to log in as any user besides root, I don't get an error, just a blank screen and then right back to the kdm login screen.

Also, it should be noted that the ftp server is not active, although ssh and tightvncserver usually are.

---

### Post by taurus on 2008-03-01
Can you also post the output of this?

```
df -h
```
Also, press <Ctrl><Alt>F2 and see if you can log in with your username and password.

---

### Post by ericinwisconsin on 2008-03-01
Oops! Yeah, 100% disk usage on the main partition... I should have guessed that, since I've been torrenting like mad the last couple of days. I moved some files to another partition and I'm fine.

Thanks for pointing me in the right direction, taurus. That was a very newbie mistake. I should have been watching my free space.

Thanks!

Eric

---

