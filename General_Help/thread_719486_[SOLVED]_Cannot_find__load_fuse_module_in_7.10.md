---
title: "[SOLVED] Cannot find / load fuse module in 7.10 ?"
date: 2008-03-09
forum: General Help
---

### Post by phrawzty on 2008-03-09
Hello,

While attempting to setup encfs on a reasonably fresh 7.10 system, i received the following error during the initial creation of an encrypted directory :

```
fuse: device not found, try 'modprobe fuse' first
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message

```

I assume the device, in this instance, is /dev/fuse ; however...

```
$ ls -l /dev/fuse
ls: /dev/fuse: No such file or directory
```

Modprobe should create this device, unfortunately...

```
$ sudo modprobe fuse
FATAL: Module fuse not found.
FATAL: Error running install command for fuse
```

Both fuse-utils and libfuse2 are installed :

```
$ dpkg -l | grep fuse
ii  fuse-utils                     2.7.0-1ubuntu5                  Filesystem in USErspace (utilities)
ii  libfuse2                       2.7.0-1ubuntu5                  Filesystem in USErspace library

```

In case the kernel version is relevant :

```
$ cat /etc/issue && uname -a
Ubuntu 7.10 \n \l

Linux sd-11222 2.6.23.10dedibox-r7 #1 Fri Dec 28 00:38:02 CET 2007 i686 GNU/Linux
```

I'm more than happy to accept any and all ideas on what the problem might be.  Thank you !

---

### Post by phrawzty on 2008-03-10
The problem was that the kernel i was using did not have the fuse headers or modules (for no apparent reason).

I attempted to use module-assistant, but it failed during the compilation phase, as described here :
[http://www.mail-archive.com/gluster-devel@nongnu.org/msg02742.html](http://www.mail-archive.com/gluster-devel@nongnu.org/msg02742.html)

The solution was as follows :

[LIST=1]
[*]Apply the patch from [http://hydra.azilian.net/blog/patches/](http://hydra.azilian.net/blog/patches/)
[*]Make a tarball from the patched source dir and replace the fuse.tar.bz2 in /usr/src
[*]Re-run module-assistant, but this time skip directly to the build phase
[*]It will compile successfully, but dpkg will fail on dependencies (related to the screwy kernel source package for my kernel)
[*]Abort the install, then manually install the generated .deb with dpkg -i --force-depends
[/LIST]

The package installs, and modprobe fuse now works properly.

---

### Post by dwnudb2282 on 2008-04-02
are there any ways to fix this without patching up the kernel & having to recompile everything ?  i'm still on Linux 2.6.22-14-generic so it doesn't look like these patches would work for me anyway ... 

basically all i'm trying to do is set up an encfs /home directory ... i installed the relevant packages, reconfigured /etc/groups, pam, /etc/security/ ,  etc ... but to no avail ... even did a "dpkg-reconfigure fuse-utils"

all my /dev/fuse & /bin/fusermount are properly configured as well ... 

is fuse just broke by default in patched versions of 7.10?  i really don't NEED  to muck about w/ encfs but i was hoping to at least have it usable without a major kernel upgrade & recompilation ...

any hints or ideas would be well appreciated ... 

thanx.

---

