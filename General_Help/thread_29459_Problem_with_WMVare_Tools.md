---
title: "Problem with WMVare Tools"
date: 2005-04-24
forum: General Help
---

### Post by jrohde on 2005-04-24
Hi all,

I'm an Ubuntu newbie, and I have just installed 5.04 on VMWare 5.0 - no problems here! But when I try to run vmware-config-tools.pl as root I keep getting this message:

The path "/usr/src/linux/include" is an existing directory, but it does not
contain at least one of these directories "linux", "asm", "net" as expected.

I have installed the kernel sources (2.6.10) in /usr/src and created the symbolic link "linux". The above mentioned include-dir is present and the direcories "linux", "asm" and "net" are also present.

What am I missing?

Thanks,

Jakob

---

### Post by jrohde on 2005-04-25
Hi again,

There must be a Linux/Ubuntu-oldie out there who knows the answer to this one!

Jakob

---

### Post by Gianni Exile on 2005-04-25
Install the linux-headers package, eg 
sudo apt-get install linux-headers-2.6.10-5-386

The symlink should be installed for you, e.g. 
```
$ ls -l /usr/src/linux
lrwxrwxrwx  1 root src 26 2005-04-10 11:55 /usr/src/linux -> linux-headers-2.6.10-5-386
$ ls /usr/src/linux
arch     fs       ipc     Makefile        net       sound
crypto   include  kernel  mm              scripts   usr
drivers  init     lib     Module.symvers  security
$
```

It works fine here.

---

