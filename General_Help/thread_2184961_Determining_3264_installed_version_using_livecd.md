---
title: "Determining 32/64 installed version using livecd"
date: 2013-10-31
forum: General Help
---

### Post by speedwlk on 2013-10-31
Hi!
Consider this hypothetical situation: You have Ubuntu [or any other distro] installed in your machine. You are currently using a Ubuntu livecd and would like to know whether the installed distro was 32-bit or 64-bit.

A roundabout solution: Assuming you are using a Debian-related distro, mount the root partition of the installed OS and look into /var/cache/apt/archives/ folder. If the accumulated source file names [.deb] contain i386 then it is 32 bit, if amd64 then it is 64 bit.

A possible usage: The grub got corrupted in the installed version and you need to reinstall grub using the livecd. You need to know whether to use a 32-bit or a 64-bit version of the livecd.

Assuming you have survived reading this huge prologue, here is my question: What are other possible ways of determining the installed OS type [from inside the livecd environment]?

Thanks in advance.

---

### Post by TheFu on 2013-10-31
mount the partition that hold /etc.
after mounting any of the partitions, find a program and run "file {path-to-program}" - that will return something like:
```
$ file /bin/gzip
/bin/gzip: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x0f8a513c140c7a145255bbdbf017b6aef2aed285, stripped

```
So, my gzip file is 32 bit.  Run it on a few other programs.

On a different machine ...
```
$ file /bin/gzip
/bin/gzip: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe144f688d03d65a26b2de66426ea63f4bbef2dd6, stripped

```

On a running system, run 'uname -a'.

There must be 100 other ways too.

---

### Post by speedwlk on 2013-10-31
@TheFu: "uname -a" from a livecd will not tell me the info I require. "uname -a" will reply regarding the livecd's kernel. That was the first thing I tried.

I am not asking this question regarding a running system.

I'll try out the "file program" command. Just for information, if grub reinstallation is required, we can try installing the 32-bit version. If it does not work, then we can go for installing the 64-bit version. I have tested this out. I just want to have a surefire way of determining the OS version before installing the grub from the livecd.

EDIT: I tested out the "file program" command. This is most certainly better than my going round to /var/cache/apt/archives/. I'll wait for a few other possible solutions. Thanks.

---

