---
title: "I can't check if fuse is activated"
date: 2015-08-28
forum: General Help
---

### Post by joan_carles2 on 2015-08-28
I'm using lubuntu 14.04. With Lubuntu I want to mount and SSHFS filesytem. I can do it without any problem and works.

The problem comes when I want to check if FUSE module is activated. The module must be activated.... Otherwise I coudln't mount the SSHFS filesystem. But if I type next command:

lsmod

I can't find anything related to fuse

If I type:

lsmod | grep fuse

Then I don't obtain any output. Just a black screen an no message,

If I type modprobe fuse 

Then I don't obtain any output. Just a black screen an no message,

Why I Can't check if fuse module is loaded on the kernel?

What should I do to check it?

---

### Post by dino99 on 2015-08-28
your post is quite confusing: the system cant run without fuse, and is active in the background 

[http://manpages.ubuntu.com/manpages/vivid/man8/mount.fuse.8.html](http://manpages.ubuntu.com/manpages/vivid/man8/mount.fuse.8.html)

---

### Post by joan_carles2 on 2015-08-28
I can use FUSE. I can use it because I can mount the SSHFS fileSystem without any problem.

My problem is that altough I can use FUSe when I list modules with lsmod... FUSE is not there. So means FUSE is not loaded... But must be loaded because I can use it.

---

### Post by steeldriver on 2015-08-28
It's likely compiled in to the kernel rather than an externally-loadable module: e.g.

```

~$ grep -i fuse /lib/modules/$(uname -r)/modules.builtin
kernel/fs/fuse/fuse.ko

```

See [http://superuser.com/questions/577307/how-to-get-a-list-of-active-drivers-that-are-statically-built-into-the-linux-ker](http://superuser.com/questions/577307/how-to-get-a-list-of-active-drivers-that-are-statically-built-into-the-linux-ker)

---

### Post by tgalati4 on 2015-08-28
Perhaps it is running as a daemon:

> tgalati4@Mint17 ~ $ ps aux | grep fuse
tgalati4  1741  0.0  0.0 345660  1016 ?        Sl   Aug22   0:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
tgalati4 11159  0.0  0.0  11744   924 pts/2    S+   08:17   0:00 grep --colour=auto fuse


I presume that* gvfsd-fuse* stands for gnome virtual file system daemon with FUSE.

---

### Post by QDR06VV9 on 2015-08-28
Yes Sir you presume right.:D

> **GVFS is the [virtual filesystem]("https://en.wikipedia.org/wiki/Virtual_filesystem") for the [GNOME desktop]("https://en.wikipedia.org/wiki/GNOME_desktop"), which allows users easy access to remote data via [SFTP]("https://en.wikipedia.org/wiki/SSH_file_transfer_protocol"), [FTP]("https://en.wikipedia.org/wiki/File_Transfer_Protocol"), [WebDAV]("https://en.wikipedia.org/wiki/WebDAV"), [SMB]("https://en.wikipedia.org/wiki/Server_Message_Block"), and local data via [Udev]("https://en.wikipedia.org/wiki/Udev")integration, [OBEX]("https://en.wikipedia.org/wiki/OBject_EXchange"), [MTP]("https://en.wikipedia.org/wiki/Media_Transfer_Protocol") and others.**
From here [https://en.wikipedia.org/wiki/GVFS](https://en.wikipedia.org/wiki/GVFS)
> [h=4]**NAME**[/h]       gvfsd-fuse - Fuse daemon for gvfs

[h=4]**SYNOPSIS**[/h]       **gvfsd-fuse** PATH

[h=4]**DESCRIPTION**[/h]       **gvfsd-fuse** maintains a fuse mount to make gvfs backends available to
       POSIX applications. The mount point for the fuse filesystem is provided [COLOR=#333333][FONT=inherit]       by the [PATH] argument.[/FONT][/COLOR]
and here [http://manpages.ubuntu.com/manpages/utopic/man1/gvfsd-fuse.1.html](http://manpages.ubuntu.com/manpages/utopic/man1/gvfsd-fuse.1.html)
Regards

---

### Post by tgalati4 on 2015-08-28
Just a lucky guess.  I came across the word *insouciant*, but I was too lazy to look it up.

---

### Post by joan_carles2 on 2015-08-29
As steeldriver says seems that FUSE is compiled with the kernel.

So in Lubuntu 14.04 seems that FUSE is load by default and it's not a module that you have to load.

Inside the file modules.builtin there is next line_


kernel/fs/fuse/fuse.ko

So he must be right.

---

