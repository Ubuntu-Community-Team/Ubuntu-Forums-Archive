---
title: "FHS - Shareable Binaries"
date: 2014-09-16
forum: General Help
---

### Post by terminator14 on 2014-09-16
I'm trying to figure out the FHS.
One of the main distinctions that the FHS makes between files is shareable vs unshareable.
While I understand that some files like man pages, and icons can be shared between systems using NFS, the entire /usr directory is classified as shareable. One of the things the /usr directory contains is /usr/bin. How can binaries be split up into shareable and unshareable categories?
At first I thought that /usr/bin would have shell scripts and static binaries that could easily be run from other systems, but this is not the case on my Debian 7 - /usr/bin mainly contains dynamically linked binaries. If this is not what makes a binary "shareable", what does?

Edit. Upon further reading, it appears that the original reason the /bin and /usr/bin directories were split up was because Ken Thompson and Dennis Ritchie physically didn't have the hard drive space to keep all the binaries on one disk. Source: [http://lists.busybox.net/pipermail/busybox/2010-December/074114.html]("http://lists.busybox.net/pipermail/busybox/2010-December/074114.html")

Some distros (like CentOS 7) have recently began combining /bin and /usr/bin, where /bin is a symlink to /usr/bin.

So does the shareable/unshareable rule the FHS talks about not apply to binaries? Are binaries just placed in /bin or /usr/bin based on where they have historically been placed?

---

### Post by matt_symes on 2014-09-16
Hi

I think shareable in this case means the files are not specific to just one machine and not that they are necessarily statically vs dynamically complied.

As one example /etc/hostname is not shareable as, in a networked environment, you only want one PC with a specific hostname.

```
matthew-laptop:/home/matthew:5 % cat /etc/hostname
matthew-laptop
matthew-laptop:/home/matthew:5 % 
```

Not currently an fqdn name i know, but...

You may want to share all the files in /usr though because, as long as all the PCs in the network are using the same version of a distribution, it can save space and maintainance if they are stored in one place only and shared via NFS.

That's my understanding of it anyway.

Kind regards

---

### Post by terminator14 on 2014-09-16
I understand that some files, like /etc/hostname must be unique to each machine and cannot be shared, while other files, like icons and man pages, can be shared freely over NFS. Icons and man pages are standalone files that do not fail to run, or be read because of missing libraries. Sharing dynamically linked binaries makes less sense to me.

My Debian 7's /usr/bin directory has files like:

eject, diff, dirname, apt-get, bc, wget, brasero, and many, many others.

What makes "eject" a shareable binary? It is dynamically linked, and wouldn't work if mounted using NFS because it needs libraries in /lib and /lib64 to be available as well. Also, the disk drive that "eject" ejects would be different on different machines.
What makes "brasero" a shareable binary? It is also dynamically linked and also won't work without a ton of libraries in /lib, and /usr/lib. If /usr was mounted over NFS, /lib on the NFS client may not have the required libraries to run brasero. The disk drive that brasero uses to burn CDs/DVDs would also be different on different machines, which may or may not be a problem.
Same goes for almost every other binary under /usr/bin, as most of them are dynamically linked and wouldn't work if only the /usr directory was mounted over NFS.

---

### Post by matt_symes on 2014-09-16
Hi

> **terminator14 said:**
> My Debian 7's /usr/bin directory has files like:

eject, diff, dirname, apt-get, bc, wget, brasero, and many, many others.

What makes "eject" a shareable binary? It is dynamically linked, and wouldn't work if mounted using NFS because it needs libraries in /lib and /lib64 to be available as well. Also, the disk drive that "eject" ejects would be different on different 

Any distribution needs a number of dynamically linked libraries regardless of whether /usr is shared or not. 

These libraries need to be on each machine regardless. NFS,  the shell, the init system uses them for a start.

My shell.

```
matthew-laptop:/usr/bin:5 % whereis zsh
zsh: /bin/zsh /usr/bin/zsh /etc/zsh /usr/bin/X11/zsh /usr/share/zsh
matthew-laptop:/usr/bin:5 % ldd /bin/zsh
        linux-vdso.so.1 =>  (0x00007fffb29fe000)
        libcap.so.2 => /lib/x86_64-linux-gnu/libcap.so.2 (0x00007fa452222000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fa45201e000)
        libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007fa451df4000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fa451aee000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa451728000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fa452444000)
matthew-laptop:/usr/bin:5 % 
```

My nfs mount.

```
matthew-laptop:/usr/bin:5 % ldd /sbin/mount.nfs4
        linux-vdso.so.1 =>  (0x00007fffd83fe000)
        libtirpc.so.1 => /lib/x86_64-linux-gnu/libtirpc.so.1 (0x00007f20cc210000)
        libmount.so.1 => /lib/x86_64-linux-gnu/libmount.so.1 (0x00007f20cbfea000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f20cbc23000)
        libgssglue.so.1 => /lib/x86_64-linux-gnu/libgssglue.so.1 (0x00007f20cba19000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f20cb7fb000)
        libblkid.so.1 => /lib/x86_64-linux-gnu/libblkid.so.1 (0x00007f20cb5d4000)
        libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f20cb3b1000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f20cc455000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f20cb1ad000)
        libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f20cafa7000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f20cad69000)
matthew-laptop:/usr/bin:5 % 
```

My init.

```
matthew-laptop:/usr/bin:5 % ldd /sbin/init
        linux-vdso.so.1 =>  (0x00007fff30ffe000)
        libnih.so.1 => /lib/x86_64-linux-gnu/libnih.so.1 (0x00007f313f5fb000)
        libnih-dbus.so.1 => /lib/x86_64-linux-gnu/libnih-dbus.so.1 (0x00007f313f3f1000)
        libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f313f1ab000)
        libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f313ef88000)
        libjson-c.so.2 => /lib/x86_64-linux-gnu/libjson-c.so.2 (0x00007f313ed7d000)
        librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f313eb74000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f313e7ae000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f313e590000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f313e351000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f313e14d000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f313fa71000)
matthew-laptop:/usr/bin:5 % 

```

Unless these are included in the initramfs there would be no way to even mount a shareable NFS so they have to be on all machines.

However, in /usr, there is a diectory specfically for dynamic libraries only used by binaries in /usr.

```

matthew-laptop:/usr/bin:5 % ls -l /usr/lib | wc -l
454
matthew-laptop:/usr/bin:5 %
``` 

These will be shared if /usr is shared.

Here is an exampl for gimp.

```
matthew-laptop:/usr/bin:5 % ldd $(readlink -f /usr/bin/gimp) | grep /usr/lib | tail -n 5
        libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fc036a4f000)
        libgraphite2.so.3 => /usr/lib/x86_64-linux-gnu/libgraphite2.so.3 (0x00007fc0365f4000)
        libdatrie.so.1 => /usr/lib/x86_64-linux-gnu/libdatrie.so.1 (0x00007fc0363ed000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fc0361e8000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fc035fe2000)
matthew-laptop:/usr/bin:5 %
```

Kind regards

---

### Post by terminator14 on 2014-09-16
> **matt_symes said:**
> Any distribution needs a number of dynamically linked libraries regardless of whether /usr is shared or not. 
These libraries need to be on each machine regardless. NFS,  the shell, the init system uses them for a start.
Unless these are included in the initramfs there would be no way to even mount a shareable NFS so they have to be on all machines.
However, in /usr, there is a diectory specfically for dynamic libraries only used by binaries in /usr.

Wow - that makes sense. Thanks
Now that I think about it, I actually had 2 questions originally:
[LIST=1]
[*]How can a dynamically linked binary even be shared when a library it may require might not be present on the NFS client?
[*]What determines if a binary is sharable, and belongs in /usr/bin, or is not shareable, and belongs elsewhere?
[/LIST]
You have answered my first question perfectly.
I am still unclear on the second - why would some binaries be considered shareable, while others not?

Another example - on my debian, I have this:
```
user@debian7:~$ readlink -f `which vi`
/usr/bin/vim.basic
user@debian7:~$ readlink -f `which nano`
/bin/nano

```

Why would vim be considered shareable, but nano considered not shareable? They both have the same purpose.
The only way this makes sense to me is if I ignore the shareable/unshareable rule for binaries and think of it as following one of these 2 rules:
[LIST=1]
[*]Which directory has vim historically been installed under? Which directory has nano historically been installed under?
[*]Which binaries are required for the system to, as the FHS document puts it, "boot, restore, recover, and/or repair the system".
Note: The FHS document is NOT talking about binaries specifically in that quote, but about the root filesystem in general, but it seems like it might explain the reasoning behind which binaries go where.
[/LIST]

Edit: Another interesting stat that supports #2 is this:

```
user@debian7:~$ du -hcs /bin /usr/bin/
7.4M	/bin
278M	/usr/bin/

```

this suggests that only essential tools are kept under /bin.
This is also consistent with this explanation: [http://unix.stackexchange.com/a/8658]("http://unix.stackexchange.com/a/8658")
Is this the true difference between /bin and /usr/bin? Does it have nothing to do with the generic rule that FHS refers to when it mentions shareable and unshareable files?

---

### Post by matt_symes on 2014-09-17
Hi

> **terminator14 said:**
> 
[LIST=1]
[*]What determines if a binary is sharable, and belongs in /usr/bin, or is not shareable, and belongs elsewhere? 
[/LIST]
You have answered my first question perfectly.
I am still unclear on the second - why would some binaries be considered shareable, while others not?

Another example - on my debian, I have this:
```
user@debian7:~$ readlink -f `which vi`
/usr/bin/vim.basic
user@debian7:~$ readlink -f `which nano`
/bin/nano

```

Why would vim be considered shareable, but nano considered not shareable? They both have the same purpose.
The only way this makes sense to me is if I ignore the shareable/unshareable rule for binaries and think of it as following one of these 2 rules:
[LIST=1]
[*]Which directory has vim historically been installed under? Which directory has nano historically been installed under? 
[*]Which binaries are required for the system to, as the FHS document puts it, "boot, restore, recover, and/or repair the system".
Note: The FHS document is NOT talking about binaries specifically in that quote, but about the root filesystem in general, but it seems like it might explain the reasoning behind which binaries go where. 
[/LIST]

Edit: Another interesting stat that supports #2 is this:

```
user@debian7:~$ du -hcs /bin /usr/bin/
7.4M    /bin
278M    /usr/bin/

```

this suggests that only essential tools are kept under /bin.
This is also consistent with this explanation: [http://unix.stackexchange.com/a/8658](http://unix.stackexchange.com/a/8658)
Is this the true difference between /bin and /usr/bin? Does it have nothing to do with the generic rule that FHS refers to when it mentions shareable and unshareable files?

You raise a very interesting question there !

You are correct when you say that only essential tools are kept under /bin. The same is true of /sbin.

As far as i'm aware, vi is considered a core part of a Unix/Linux system and is available on almost all Linux distributions from router firmware such as dd-wrt to standard Linux, BSD and Solaris installations.

This is why it's so useful to know a little vi. It's the only editor on my dd-wrt flashed router - that's vi and not vim.

I cannot tell you why vi is stored under /usr/bin and not under /bin on Debian and Ubuntu.

I can only speculate that it may be due to security reasons - it can easily be removed from an NFS shared /usr - but only the maintainers/packagers can tell you exactly why this is the case; i suspect my supposition is wrong in any case.

As to why nano is in /bin, a distribution will always need at least one editor in /bin and i suspect the default editor is nano as the learning curve for nano is much lower that vi.

Kind regards

---

### Post by terminator14 on 2014-09-17
After reading several online articles, and continuing to read the FHS v2.3, it appears that the division of binary files between the root filesystem (/bin and /sbin) and /usr subdirectories (/usr/bin, /usr/sbin) really has nothing to do with their shareability, and everything to do with the 2 things mentioned earlier:

1. Where has the binary historically been placed?
2. Is the binary essential to "boot, restore, recover, and/or repair the system".

I've also found the section in the FHS document that states exactly what you said - /lib is for libraries used by binaries in /bin and /sbin, and /usr/lib is for libraries used by /usr/bin and /usr/sbin.
I imagine you are right about the decision to place nano into /bin, and vim into /usr/bin - nano is easier to use, and you only need one text editor to recover a system.
Side note: I've been studying vim like crazy the past few weeks - it's pretty interesting the crazy things it can do. I am also surprised it's not included in /bin - I've also seen vi (vim) on many embeded systems that didn't even have nano.
And as steep a learning curve as vim has, vi is so much worse! Last time I tried pure vi (it might have just been vim in compatibility mode), it wouldn't even tell you what mode you were in! And only one level of undo? What's up with that? I kind of like vim, but really hate vi.

Anyway, thanks for helping me clear this up Matt.

---

