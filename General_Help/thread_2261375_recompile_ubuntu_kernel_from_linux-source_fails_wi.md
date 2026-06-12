---
title: "recompile ubuntu kernel from linux-source fails with debian/rules . ok with make-kpkg"
date: 2015-01-18
forum: General Help
---

### Post by interzoneuk on 2015-01-18
Hi

I am trying to recompile the Ubuntu patched kernel (not vanilla kernel) - I am using 14.10.

Before anyone starts going on about why ? its due to 

- lack of oss (old OSS) sound modules meaning not sound of some (old) games - aoss and pdoss doesn't work with the games/my H/W (having the kernel OSS modules is the ONLY way to play some old games - i.e paintball2 (SDL is broken)
- removal of nouveau 
- choose the typeof CPU (rather than generic x86_64) - even if that only improves performance by 0.5 % thats better than no improvement
- I also remove XEN support
- set to 1000Hz
- I want to ....

I can create the kernel package find if I do the following fine (method1 - make-kpkg)

method1:-
-------------
```
apt-get source linux-image-$(uname -r) 
dpkg-source -x *.dsc
cd linux-3.16.0/
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
cp /boot/config-`uname -r` .config
fakeroot debian/rules clean
make menuconfig  (make my modifications)
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

- this works fine - builds kernel/image packages and it works.

Method 2 :
----------------

outlined [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

```
apt-get source linux-image-$(uname -r)
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
fakeroot debian/rules editconfigs
--> modify the first choice - amd64-generic.

fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic
```

It goes through the whole build process then stops at
```

Debug: module-check-generic
install -d /home/morgan/src_2/linux-3.16.0/debian.master/abi/3.16.0-29.39/amd64
find /home/morgan/src_2/linux-3.16.0/debian/build/build-generic/ -name \*.ko | \
	sed -e 's/.*\/\([^\/]*\)\.ko/\1/' | sort > /home/morgan/src_2/linux-3.16.0/debian.master/abi/3.16.0-29.39/amd64/generic.modules
II: Checking modules for generic...
   reading new modules...read 4118 modules.
   reading old modules...
      MISS: nouveau
      MISS: r128
      MISS: radeon
      MISS: sis-agp
      MISS: tdfx
      MISS: tmem
      MISS: xen-blkback
      MISS: xen-evtchn
      MISS: xen-fbfront
      MISS: xenfs
      MISS: xen-gntalloc
      MISS: xen-gntdev
      MISS: xen-kbdfront
      MISS: xen-netback
      MISS: xen-pciback
      MISS: xen-pcifront
      MISS: xen-privcmd
      MISS: xen-tpmfront
      MISS: xen_wdt
      NEW : sound
      NEW : sound_firmware
      NEW : v_midi
      NEW : snd-pcm-oss
      NEW : snd-seq-oss
      read 4132 modules : new(5)  missing(19)
EE: Missing modules (start begging for mercy)
debian/rules.d/4-checks.mk:12: recipe for target 'module-check-generic' failed
make: *** [module-check-generic] Error 1
```

any ideas why it fails here?

---

### Post by Doug S on 2015-01-18
First, I'll say that I do not know the answer to your actual question.

There seems to be several different ways to compile the kernel. My experience has been that several of the methods are excessively complicated, while claiming to be simple, and do not provide any information at all as to why a build exits with an error, and one is left with no idea how to proceed. It is just my opinion, but I have had the best success using the "[old-fashioned debian way"]("https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method_.28B.29:_The_Old-Fashioned_Debian_Way"), including meaningful error messages upon error exit when I make mistakes.

Note that now I actually just steal the Ubuntu kernel configuration and compile the code from kernel.org, obtained via git.

I don't know if this post will help or just add confusion.

---

### Post by interzoneuk on 2015-01-18
Hi.

Cheers for the response, much appreciated.

I am familiar with the method you linked to, I used to build kernel's from kernel.org using that method.

I was after all the ubuntu patches also.

I also used to use this method - via git - make a new branch (i.e i5) 

[http://blog.avirtualhome.com/how-to-compile-a-new-ubuntu-11-04-natty-kernel/](http://blog.avirtualhome.com/how-to-compile-a-new-ubuntu-11-04-natty-kernel/)  

--> but that was far far far more hassle than just download source use make-kpkg ...

---

### Post by mc4man on 2015-01-18
No clue really but the error seems fairly clear. Your build source started with a list of modules (generic.modules). The build produced 5 new (not listed) & didn't produce 19 (Miss).
Why, no idea. Maybe from your changes & or building locally. 

If your build created a log maybe you could read back & see why.
I guess if it were me I may try adjusting that .modules file in a new or cleaned source & see what happens. (remove the missing, add the new.
(- if you need the nouveau or radeon modules then ^  isn't going to prove that useful

---

### Post by apw on 2015-01-19
> **interzoneuk said:**
> Hi
II: Checking modules for generic...
   reading new modules...read 4118 modules.
   reading old modules...
      MISS: nouveau
[...]
      read 4132 modules : new(5)  missing(19)
EE: Missing modules (start begging for mercy)
debian/rules.d/4-checks.mk:12: recipe for target 'module-check-generic' failed
make: *** [module-check-generic] Error 1[/CODE]

any ideas why it fails here?

It is being pretty clear in its error message that previously built modules, modules built in the previous upload, are now missing.  This is a fatal error for distro uploads.  You would need to either inform it that those modules are expected to be missing, but cleaning up the modules files in debian.master/abi, or disable module checks with skip_modules=1

---

