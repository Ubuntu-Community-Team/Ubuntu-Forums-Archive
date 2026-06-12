---
title: "User can access file, root can't?"
date: 2008-07-03
forum: General Help
---

### Post by lawtech on 2008-07-03
I thought there was NOTHING root couldn't do. Can somebody please shed some light on this "Permission denied" matter?

I first ran into this message when a '# cp -a /home /target' blew up, and I had to work around it. The 'ls' below gives a simpler case.

$ sudo -s
# ls -la ~/.gvfs
ls: cannot access /home/nick/.gvfs: Permission denied
# ls -la ~
... (omitted)
-rw-r--r--  1 nick nick   104 2008-06-28 10:26 .gtk-bookmarks
d?????????  ? ?    ?        ?                ? .gvfs
drwxr-----  2 nick nick  4096 2008-06-20 11:39 .hplip
... (omitted)
# exit
$ ls -la ~/.gvfs
total 4
dr-x------  2 nick nick    0 2008-06-28 10:06 .
drwxr-xr-x 49 nick nick 4096 2008-07-03 08:26 ..
[email]nick@black-host:~/.gvfs[/email]$ 
$ ls -la ~
... (omitted)
-rw-r--r--  1 nick nick   104 2008-06-28 10:26 .gtk-bookmarks
dr-x------  2 nick nick     0 2008-06-28 10:06 .gvfs
drwxr-----  2 nick nick  4096 2008-06-20 11:39 .hplip
... (omitted)


$ uname -a
Linux black-host 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
$ cat /etc/issue
Ubuntu 8.04.1 \n \l

---

### Post by eldragon on 2008-07-03
i would schedule a fsck on that partition as a first measure.

---

### Post by justleen on 2008-07-03
how bout doing a "sudo -k", or "sudo su"?

---

### Post by lawtech on 2008-07-03
# tune2fs -C 99 /dev/sda1 (containing /)
# tune2fs -C 99 /dev/sda5 (containing /home)
# shutdown -h now

On reboot, the fsck ran on both partitions and showed no errors.

The reported behavior remains.

$ sudo su
# ls -la /home/nick/.gvfs
ls: cannot access /home/nick/.gvfs: Permission denied
# exit
$ sudo -k
[sudo] password for nick: (given)
$ sudo ls -la .gvfs/
ls: cannot access .gvfs/: Permission denied
$ sudo ls -la ~
ls: cannot access /home/nick/.gvfs: Permission denied
$ ls -la .gvfs/
total 4
dr-x------  2 nick nick    0 2008-07-03 09:48 .
drwxr-xr-x 49 nick nick 4096 2008-07-03 09:48 ..

---

### Post by lawtech on 2008-07-03
Thanks to Alexander Larsson at Red Hat, I now have more information. Alex is evidently the author/maintainer of gvfs. Here is an old thread with quite a bit of info:

[http://mail.gnome.org/archives/gtk-devel-list/2007-February/msg00062.html]("http://mail.gnome.org/archives/gtk-devel-list/2007-February/msg00062.html")

Alex tells me that this is a FUSE issue. He says, "~/.gvfs is the fuse filesystem that shows current gvfs mounts," and he gives this reference:

[http://fuse.sourceforge.net/wiki/index.php/FAQ]("http://fuse.sourceforge.net/wiki/index.php/FAQ")

specifically the "Why don't other users have access to the mounted filesystem?" question, which says in part:

"FUSE imposes this restriction in order to protect other users' processes from wandering into a FUSE filesystem that does nasty things to them such as stalling their system calls forever."

It goes on to provide a link into the sourceforge code and a way to defeat the restriction, although doing so doesn't sound like a very good idea to me.

So I guess you *can* keep root out of *some* things.

---

