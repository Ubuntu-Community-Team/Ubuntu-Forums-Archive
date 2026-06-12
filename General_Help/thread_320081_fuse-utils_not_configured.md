---
title: "fuse-utils not configured?"
date: 2006-12-16
forum: General Help
---

### Post by artinla on 2006-12-16
Anyone have any ideas why this fails?  I am in a chroot jail adding some updates to a livecd extracted filesystem (using reconstructor).  Everything else works fine.  BTW it is an edgy system.


root@fettbauch:/# sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fuse-utils
The following NEW packages will be installed:
  fuse-utils ntfs-3g
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 87.7kB of archives.
After unpacking 295kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ntfs-3g
Install these packages without verification [y/N]? y
Get:1 [http://givre.cabspace.com](http://givre.cabspace.com) edgy/main ntfs-3g 1:0.20061031-BETA-2 [31.0kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main fuse-utils 2.5.3-2.1ubuntu4 [56.6kB]
Fetched 87.7kB in 0s (96.0kB/s)                               
Selecting previously deselected package fuse-utils.
(Reading database ... 159821 files and directories currently installed.)
Unpacking fuse-utils (from .../fuse-utils_2.5.3-2.1ubuntu4_i386.deb) ...
Selecting previously deselected package ntfs-3g.
Unpacking ntfs-3g (from .../ntfs-3g_1%3a0.20061031-BETA-2_i386.deb) ...
Setting up fuse-utils (2.5.3-2.1ubuntu4) ...
creating fuse device...
creating fuse group...
Adding group `fuse' (114)...
Done.
FATAL: Could not load /lib/modules/2.6.17-10-386/modules.dep: No such file or directory
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ntfs-3g:
 ntfs-3g depends on fuse-utils (>= 2.5); however:
  Package fuse-utils is not configured yet.
dpkg: error processing ntfs-3g (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fuse-utils
 ntfs-3g
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@fettbauch:/#


I think it is because the liveCD filesystem uses kernel version 2.6.17-10-generic instead of 2.6.17-10-386.  Any ideas on how to get around this?

Thanks

---

### Post by artinla on 2006-12-18
Bump.

I can't remember the last time that I actually got a reply on these forums.

Maybe the hundredth try will be the charm.

---

### Post by christhemonkey on 2006-12-18
The only thing i can think of is try installing that kernel first?
Then running that command and finally removing the extra kernel.

---

### Post by artinla on 2006-12-19
Thanks for the reply.

Actually the -generic IS the kernel in my chroot environment.  Somehow, and i don't understand why, the fuse-utils installer is assuming that I have the -386 kernel.   I am wondering if I need to set some environment variable to tell the fuse installer which kernel I am using in the chroot.  

So to clarify..  My system boots into a -386 kernel, I am chrooting into a filesystem that uses a -generic kernel.  Inside the chroot, the fuse installer is confused and thinks that I need the -386 version, when I really want to install it for the -generic kernel.

I am wondering if I can set an environment variable inside the chroot to pass the proper  kernel information to the fuse installer.


BTW, with reconstructor I have made some really nice customized Edgy LiveCD's.  All the codecs, fonts, apps, etc. already installed and ready to go.  I would love to add the NTFS r/w support, but it isn't mandatory.

---

### Post by christhemonkey on 2006-12-19
Could try something like:
```
export KERNEL_VERSION="2.6.17-10-386"
```

But that probably wont work...
The problem being that it is looking for a file found in the kernel image that you dont have installed in the chroot.  You could always sym-link it there?

```
sudo ln -s /lib/modules/2.6.17-10-generic/modules.dep /lib/modules/2.6.17-10-386/modules.dep 
```
Though you might have to make the directorys first...

---

### Post by artinla on 2006-12-23
I installed linux-image-2.6.17-10-386 into my chroot and then fuse-utils and nfs3g installed fine.  Now I have to recompress the liveCD filesystem to see if it still works OK with the extra kernel.  That takes a while but I will let you know if it works. 

Thanks for the suggestions.

Art

---

