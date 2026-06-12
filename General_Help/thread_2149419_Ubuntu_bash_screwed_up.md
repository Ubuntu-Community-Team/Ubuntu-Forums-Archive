---
title: "Ubuntu bash screwed up"
date: 2013-05-28
forum: General Help
---

### Post by chiques on 2013-05-28
Hello Everyone,
I'm fiddling with securing an ssh account and I think I might have screwed up my bash settings on my administrator account. I'm using 'user1' (my admin account) to jail 'user2' my ssh sharing account (for ftp sharing within my family).

I followed [this tutorial]("http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/") to restrict my user2 account but now when I log in to my user1 account I get this:
> 
Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

New release 'precise' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Tue May 28 13:40:31 2013 from ~snip~
-bash: getent: command not found
-bash: cut: command not found
-bash: expr: command not found
user1@ubuntu-desktop



I am compleltley locked out from running > sudo su, > sudo -i or any other sudo access.

The error I get is:
> -bash: /usr/bin/python: Permission denied


Is there a way to restore my bash access or am I hosed and require a re-format?

P.S. I have not activated the 'root' account.

---

### Post by papibe on 2013-05-28
Hi chiques.

Could you post the output of these 2 commands?
```
/bin/ls -l /bin/bash /bin/rbash

/bin/grep user1 /etc/passwd
```
Regards.

---

### Post by chiques on 2013-05-28
> **papibe said:**
> Hi chiques.

Could you post the output of these 2 commands?
```
/bin/ls -l /bin/bash /bin/rbash

/bin/grep user1 /etc/passwd
```
Regards.

```

user1@user1-desktop:~$ /bin/ls -l /bin/bash /bin/rbash
-rwxr-xr-x 1 root root 818232 2010-04-18 18:51 /bin/bash
lrwxrwxrwx 1 root root      4 2010-06-20 23:24 /bin/rbash -> bash
user1@user1-desktop:~$
```


```

user1@user1-desktop:~$ /bin/grep user2 /etc/passwd
user2:x:1001:100:user2,,,,:/home/user2:/bin/rbash
user1@user1-desktop:~$

```

---

### Post by papibe on 2013-05-28
Thanks. It looks OK.

Is user1 using bash or rbash?
```
/bin/grep **user1** /etc/passwd
```
Regards.

---

### Post by chiques on 2013-05-28
> **papibe said:**
> Thanks. It looks OK.

Is user1 using bash or rbash?
```
/bin/grep **user1** /etc/passwd
```
Regards.

```

user1@user1-desktop:~$ /bin/grep user1 /etc/passwd
user1:x:1000:1000:user1,,,:/home/user1:/bin/bash
user1@user1-desktop:~$

```

I guess this means I'm using bash???

---

### Post by papibe on 2013-05-28
Yes.

Make sure you didn't remove your own config files (user1's .bashrc.  .profile, etc).

Regards.

---

### Post by chiques on 2013-05-29
> **papibe said:**
> Yes.

Make sure you didn't remove your own config files (user1's .bashrc.  .profile, etc).

Regards.

Too late. I read a forum post that recommended to remove those files. Now the system is really hosed. I'll just backup and reformat- less time.

---

### Post by steeldriver on 2013-05-30
if you've only removed user config files, that really shouldn't be necessary

perhaps all you need to do in the first instance is to reset your PATH environment variable so that your shell can find the basic executables (ls, cp,  etc) and then make fresh copies of /etc/skel/.profile and /etc/skel/.bashrc

or even just (from your user's home directory)

```
/bin/cp -t . /etc/skel/{.bash_logout,.bashrc,.profile}
```

---

