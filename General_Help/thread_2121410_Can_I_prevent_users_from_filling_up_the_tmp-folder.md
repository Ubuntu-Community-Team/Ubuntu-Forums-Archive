---
title: "Can I prevent users from filling up the /tmp-folder?"
date: 2013-03-01
forum: General Help
---

### Post by Bufeu on 2013-03-01
A normal user has read and write access to the /tmp-folder. If someone decides to "block" other users from using the system, the person can just fill up the /tmp-folder until it's full (with *echo /dev/null>/tmp/bigfile* or something like that), so no other user can write data to it (simply because it's full). Can I limit how much size, as maximum, of a certain mounting point (in this case /tmp) a user can use? Do I need to have /tmp on its own partition? It is possible to limit all files in the ~ (a user's home folder) to a maximum at, let's say 0.5 GiB, excluded the .thunderbird-folder (in other words, the content in the .thunderbird-folder will not included in the limit at 0.5 GiB)?

---

### Post by pqwoerituytrueiwoq on 2013-03-01
if a user is filling up /tmp/ intentionally they would just be able to do it in the sub folder .thunderbird-folder (why is that in /tmp anyway?)
you can move /tmp to another drive/partition/ram easily using fstab, but if that filled up there would still be issues
not sure of a way to limit there data in /tmp

---

### Post by matt_symes on 2013-03-01
Hi

Mount /tmp on its own partition and use per user disk quotas ?

[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html)

I believe that's quite standard practice.

Kind regards

---

### Post by rnerwein on 2013-03-02
hi
ok that's a solution for that "little" problem. but i think there are much bigger problems. 
just run: ulimit -a
i know you now wath i mean.
i predict this my customer since years. you have to occupy a system (talking about servers) to now what is the normal behavior. oh yeah this is expansive (it only looks like :-) ). 
have a nice day
ciao

---

### Post by Bufeu on 2013-03-02
> **pqwoerituytrueiwoq said:**
> if a user is filling up /tmp/ intentionally they would just be able to do it in the sub folder .thunderbird-folder (why is that in /tmp anyway?)
you can move /tmp to another drive/partition/ram easily using fstab, but if that filled up there would still be issues
not sure of a way to limit there data in /tmpNo. The .thunderbird-folder is in the ~-folder (/home/.../.thunderbird). I want to limit the usage of /tmp and /home (but not ~/.thunderbird).

---

### Post by rnerwein on 2013-03-02
hi bufeu
matt_syms allready gave you the correct answer - use quotas.
cheers

---

### Post by Bufeu on 2013-03-02
> **rnerwein said:**
> hi bufeu
matt_syms allready gave you the correct answer - use quotas.
cheersYes, I saw it. That means I can only enable a limit on a whole partition, not only a directory?

---

### Post by matt_symes on 2013-03-02
Hi

I would be mounting /tmp on its own partition anyway, in a multi-user environment.

As far as i'm aware, quotas are based on filesystems and not directories. (at least in ExtX filesystems)

I am open to correction though.

Kind regards

---

### Post by schragge on 2013-03-02
Well, I guess it's possible to exclude *~/.thunderbird* from quota, but you will have to maintain a symlink farm for this.
That is, you will have so to say two /home hierarchies: one for user home directories as usual, another, on a separate filesystem, for their *.thunderbird* subdirs. The disk quota is then turned on only on */home*.

If you don't use NFS for automounting user home directories then it'll be enough to put into */usr/local/sbin/adduser.local* something like
```

mkdir /.thunderbird/$1
chown $1: /.thunderbird/$1
ln -s /.thunderbird/$1 $4/.thunderbird

``` for corresponding /.thunderbird/*username* directory to be created and symlinked automatically when adding new users.

See [adduser(8)](http://manpages.ubuntu.com/manpages/precise/en/man8/adduser.8.html) for description of the */usr/local/sbin/adduser.local* script and its parameters.

---

### Post by rnerwein on 2013-03-02
hi
i would say you can set it per user inside of a filesystem.
i am open too for correction ;-)
ciao

---

### Post by Bufeu on 2013-03-02
> **schragge said:**
> Well, I guess it's possible to exclude *~/.thunderbird* from quota, but you will have to maintain a symlink farm for this.
That is, you will have so to say two /home hierarchies: one for user  home directories as usual, another, on a separate filesystem, for their *.thunderbird* subdirs. The disk quota is then turned on only on */home*.

If you don't use NFS for automounting user home directories then it'll be enough to put into */usr/local/sbin/adduser.local* something like
```

mkdir /.thunderbird/$1
chown $1: /.thunderbird/$1
ln -s /.thunderbird/$1 $4/.thunderbird

``` for corresponding /.thunderbird/*username* directory to be created and symlinked automatically when adding new users.

See [adduser(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/adduser.8.html") for description of the */usr/local/sbin/adduser.local* script and its parameters.Thanks. :D

---

