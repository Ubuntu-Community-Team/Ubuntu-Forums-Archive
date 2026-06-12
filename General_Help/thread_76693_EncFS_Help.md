---
title: "EncFS Help?"
date: 2005-10-15
forum: General Help
---

### Post by Pig Monkey on 2005-10-15
I'm attempting to get [encfs]("http://arg0.net/wiki/encfs") working with 5.10. After I do *sudo apt-get install encfs*, create the encrypted disk (*encfs /tmp/raw /tmp/crypt*), and enter my password, I get the following error:
```
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
```

If I run it as root, it works fine. Any ideas how I can make fusermount work with normal users?

---

### Post by Wombley on 2005-10-15
[QUOTE=Pig Monkey]I'm attempting to get [encfs]("http://arg0.net/wiki/encfs") working with 5.10. After I do *sudo apt-get install encfs*, create the encrypted disk (*encfs /tmp/raw /tmp/crypt*), and enter my password, I get the following error:
```
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
```

If I run it as root, it works fine. Any ideas how I can make fusermount work with normal users?[/QUOTE]

I'm not using 5.10 yet, but on Hoary I found that fusermount was installed so only root could execute it - try ```
$ sudo chmod +x /usr/bin/fusermount
```

---

### Post by Pig Monkey on 2005-10-15
That fixed it! Thanks.

---

### Post by mbwardle on 2005-10-28
I had the same problem when trying to get the Bluetooth File System "btfs" working.  What I don't get is why fusermount doesn't work in the default configuration if I'm a member of the "fuse" group:

> ls -l /usr/bin/fusermount
-rwsr-xr--  1 root fuse 16984 Jul 25 00:57 /usr/bin/fusermount

> groups | grep -c fuse
1

> fusermount
zsh: permission denied: fusermount

It seems to get setuid working, the file has to be executable by "other" (chmod o+x), even tho it would take my effective access permissions from the "group" bits.  I didn't think things worked like this.

---

### Post by mark541 on 2005-12-15
[QUOTE=mbwardle]I had the same problem when trying to get the Bluetooth File System "btfs" working.  What I don't get is why fusermount doesn't work in the default configuration if I'm a member of the "fuse" group:

> ls -l /usr/bin/fusermount
-rwsr-xr--  1 root fuse 16984 Jul 25 00:57 /usr/bin/fusermount

> groups | grep -c fuse
1

> fusermount
zsh: permission denied: fusermount

It seems to get setuid working, the file has to be executable by "other" (chmod o+x), even tho it would take my effective access permissions from the "group" bits.  I didn't think things worked like this.[/QUOTE]
I was able to use "fusermount" once I was a member of the group "fuse". However, I had to log out (not just the terminal, out of X too). Once I did that and logged back in, I was OK.

---

### Post by IAmAI on 2007-01-12
I found I also had to change the group of 'dev/fuse' to 'fuse' otherwise I'd get the following error message:

```
fusermount: failed to open /dev/fuse: Permission denied
```

What I'm finding strange is that I didn't have to perform all this manual configuration last time I installed sshfs, prior to reinstalling Kubuntu. From what I can recall, it all seemed to work straight away.

---

### Post by sudenaz on 2007-01-12
I'm not using 5.10 yet, but on Hoary I found that fusermount was installed so only root could execute it - try 
look
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by Rich43 on 2007-04-22
Make yourself a member of the fuse group.

---

### Post by louisgag on 2007-06-25
...or make the group of /dev/fuse  yours

---

### Post by julian67 on 2007-10-03
[https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212]("https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212")

> Bug description [edit]

fuse (sshfs, encfs, ... ) fails reporting:

fusermount: failed to open /dev/fuse: Permission denied

This is because /dev/fuse is group root, when it should be group fuse
Workaround:

sudo chgrp fuse /dev/fuse

and all is well.



I spent a day not being able to make encfs work. I eventually looked in the right place and this fixed it immediately. Posted this so anyone else can google and find the solution to their permission problems with fuse filesystems and dependent applications.

---

### Post by OmahaVike on 2007-10-16
> **Wombley said:**
> I'm not using 5.10 yet, but on Hoary I found that fusermount was installed so only root could execute it - try ```
$ sudo chmod +x /usr/bin/fusermount
```

Dapper user here, with the exact same problem -- root user works fine, regular user does not, even when using it on home directory.

1)  fusermount is already set for execute for all 
2)  /dev/fuse group is set to fuse
3)  user is in the fuse group

Any other things I could try?

TIA!

---

### Post by julian67 on 2007-10-16
> **OmahaVike said:**
> Dapper user here, with the exact same problem -- root user works fine, regular user does not, even when using it on home directory.

1)  fusermount is already set for execute for all 
2)  /dev/fuse group is set to fuse
3)  user is in the fuse group

Any other things I could try?

TIA!

add the line ```
chgrp fuse /dev/fuse
``` to /etc/init.d/fuse right after "### END INIT INFO" and when you reboot it should be fixed.

---

### Post by OmahaVike on 2007-10-16
> **julian67 said:**
> add the line ```
chgrp fuse /dev/fuse
``` to /etc/init.d/fuse right after "### END INIT INFO" and when you reboot it should be fixed.

Thank you for the reply Julian67.

There is no such file in that directory.  Here's the results of a find:

```

/dev/fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse
/lib/modules/2.6.15-27-386/kernel/fs/fuse
/lib/modules/2.6.15-28-386/kernel/fs/fuse
/sys/module/fuse
/sys/class/misc/fuse
/usr/include/fuse
/usr/src/linux-headers-2.6.15-28/include/config/fuse
/usr/src/linux-headers-2.6.15-28/fs/fuse
/usr/src/modules/fuse
/usr/src/linux-headers-2.6.15-28-386/include/config/fuse

```

I tried to make it from source, but it tells me that it's already present in the kernel.

And here is the result of a find on fuse*
```

/var/cache/apt/archives/fuse-source_2.4.2-0ubuntu3_all.deb
/var/cache/modass/fuse-source.avail_version
/var/lib/dpkg/info/fuse-source.md5sums
/var/lib/dpkg/info/fuse-source.list
/var/lib/dpkg/info/fuse-utils.config
/var/lib/dpkg/info/fuse-utils.list
/var/lib/dpkg/info/fuse-utils.templates
/var/lib/dpkg/info/fuse-utils.postinst
/var/lib/dpkg/info/fuse-utils.postrm
/var/lib/dpkg/info/fuse-utils.conffiles
/var/lib/dpkg/info/fuse-utils.md5sums
/etc/default/fuse-utils
/bin/fuser
/dev/fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse
/lib/modules/2.6.15-23-386/kernel/fs/fuse/fuse.ko
/lib/modules/2.6.15-27-386/kernel/fs/fuse
/lib/modules/2.6.15-27-386/kernel/fs/fuse/fuse.ko
/lib/modules/2.6.15-28-386/kernel/fs/fuse
/lib/modules/2.6.15-28-386/kernel/fs/fuse/fuse.ko
/sys/module/fuse
/sys/class/misc/fuse
/usr/bin/fusermount
/usr/include/fuse
/usr/include/fuse/fuse_compat.h
/usr/include/fuse/fuse.h
/usr/include/fuse/fuse_common.h
/usr/include/fuse/fuse_lowlevel.h
/usr/include/fuse.h
/usr/lib/pkgconfig/fuse.pc
/usr/share/doc/fuse-utils
/usr/share/doc/fuse-source
/usr/share/doc/libfuse-dev/examples/fusexmp.c
/usr/share/man/man1/fuser.1.gz
/usr/share/man/man1/fusermount.1.gz
/usr/share/fuse-utils
/usr/src/linux-headers-2.6.15-28/include/linux/fuse.h
/usr/src/linux-headers-2.6.15-28/include/config/fuse
/usr/src/linux-headers-2.6.15-28/fs/fuse
/usr/src/modules/fuse
/usr/src/modules/fuse/kernel/fuse_i.h
/usr/src/modules/fuse/kernel/fuse_kernel.h
/usr/src/modules/fuse/include/old/fuse.h
/usr/src/modules/fuse/include/fuse.h
/usr/src/modules/fuse/include/fuse_compat.h
/usr/src/modules/fuse/include/fuse_common.h
/usr/src/modules/fuse/include/fuse_lowlevel.h
/usr/src/modules/fuse/include/fuse_kernel.h
/usr/src/modules/fuse/debian/fuse-module-_KVERS_.postinst.modules.in
/usr/src/linux-headers-2.6.15-28-386/include/linux/fuse.h
/usr/src/linux-headers-2.6.15-28-386/include/config/fuse
/usr/src/fuse.tar.bz2

```

(which, as you can see, includes fuse-utils)

FYI:  I followed the how-to from here.  [http://ubuntuforums.org/showthread.php?t=148600]("http://ubuntuforums.org/showthread.php?t=148600")

Thanks again for your help.

---

### Post by julian67 on 2007-10-16
I guess I did it the easy way :-) I have fuse installed because I want ntfs read/write capability and so I install ntfs-3g via Synaptic very soon after OS install. I believe this takes care of most issues except the one I mentioned. And for a tool for creating/managing encrypted containers I find installing Cryptkeeper from deb is the simplest way to do it. I particularly like it as it can be set up to unmount the encfs container after it is idle for a specified time...and everything is done with a few clicks in dialogues, very slick and easy.

---

