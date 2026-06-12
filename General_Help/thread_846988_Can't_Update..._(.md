---
title: "Can't Update... :("
date: 2008-07-02
forum: General Help
---

### Post by gerankle on 2008-07-02
Well, I was having trouble with permission and crap but I fixed that, but now I get this message when I try to update.

```
Preconfiguring packages...
dpkg: unable to install new triggers deferred file `/var/lib/dpkg/triggers/Unincorp': No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
```

Help me! :(

---

### Post by Blindraven on 2008-07-02
[http://ubuntuforums.org/showthread.php?t=808875](http://ubuntuforums.org/showthread.php?t=808875)

---

### Post by iaculallad on 2008-07-02
Try to touch the missing file or directory:

```
sudo touch /var/lib/dpkg/triggers/Unincorp
sudo dpkg --configure -a
```

---

### Post by gerankle on 2008-07-02
Terminal gave me:

```
touch: cannot touch `/var/lib/dpkg/triggers/Unincorp': No such file or directory

```

and

```
dpkg: status database area is locked by another process

```

---

### Post by iaculallad on 2008-07-02
Try relating with this [thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4369682"), you got similar problem.

---

### Post by gerankle on 2008-07-02
my unincorp file was blank like it's supposed to be... :(

---

### Post by gerankle on 2008-07-02
OK, so i was able to create "unincorp" (same name as file in there before)

I found out I am missing Unincorp (with a capital U). How do I go about creating or acquiring this file and putting it in?

```
stewie@stewie-desktop:~$ ls -la /var/lib/dpkg/triggers
ls: cannot access /var/lib/dpkg/triggers/Unincorp: No such file or directory
total 20
drwxr-xr-x 2 root root 4096 2008-07-02 00:49 .
drwxr-xr-x 7 root root 4096 2008-07-02 00:49 ..
-rw-r--r-- 1 root root    6 2008-07-02 00:49 ldconfig
-rw------- 1 root root    0 2008-07-02 00:49 Lock
-rw-r--r-- 1 root root    0 2008-07-02 00:15 new file~
-rw-r--r-- 1 root root    0 2008-07-02 00:34 unincorp
-????????? ? ?    ?       ?                ? Unincorp
-rw-r--r-- 1 root root    0 2008-07-02 00:49 Unincorp.new
-rw-r--r-- 1 root root    0 2008-07-02 00:11 Unincorp.new~
-rw-r--r-- 1 root root    5 2008-07-02 00:49 update-grub
-rw-r--r-- 1 root root   16 2008-07-02 00:49 update-initramfs
stewie@stewie-desktop:~$ 

```

---

### Post by gerankle on 2008-07-02
sorry to bump, but not being able to install/uninstall anything kind of sucks :(.

---

### Post by plucky on 2008-07-03
Did a search of "unincorp" and found this [Thread](http://ubuntuforums.org/showthread.php?p=4401439&highlight=Unincorp#post4401439)

Good Luck

---

### Post by gerankle on 2008-07-04
I can't even do this:

```
sudo apt-get remove libsdl-ttf2.0-0
```

says Unincorp doesn't exist.

Dangit, what should I do? Should i just reinstall ubuntu?

---

