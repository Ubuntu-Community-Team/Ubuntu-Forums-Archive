---
title: "Can't compile linux-restricted-modules"
date: 2007-05-05
forum: General Help
---

### Post by thetorpedodog on 2007-05-05
I've been struggling with compiling linux-restricted-modules for a custom kernel I made which has [HDAPS support with queuefreeze and tp_smapi](http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS).

I've compiled it per [the wiki page on compiling your kernel](https://wiki.ubuntu.com/KernelCustomBuild) (the kernel itself works flawlessly).

Here, for your information, is my debian/d-i/kernel-versions.in```
# arch   version    flavour       installedname            suffix build-depends
i386     @@ABIVER@@  ttid-hdaps           @@ABIVER@@-ttdi-hdaps              -	
#i386     @@ABIVER@@  generic       @@ABIVER@@-generic          -	
#powerpc  @@ABIVER@@  powerpc       @@ABIVER@@-powerpc          -	
#amd64    @@ABIVER@@  generic       @@ABIVER@@-generic          -	
```
And the difference between my debian/rules and the default:
```
116,118c116,118
< flavours := $(addprefix $(kernel_abi_version)-,ttdi-hdaps)
< vmware_server_extra_flavours := $(addprefix $(kernel_abi_version)-,)
< vmware_tools_extra_flavours := $(addprefix $(kernel_abi_version)-,)
---
> flavours := $(addprefix $(kernel_abi_version)-,generic 386 lowlatency)
> vmware_server_extra_flavours := $(addprefix $(kernel_abi_version)-,server server-bigiron)
> vmware_tools_extra_flavours := $(addprefix $(kernel_abi_version)-,server)

```
ttdi-hdaps is the name that I've given to my kernel variation, so it's "2.6.20-15-ttdi-hdaps" in full. It's on the i386 architecture (Pentium M variant, since my Thinkpad has a Core Duo).

The build process usually fails around here (this is make's output):
```
                /usr/bin/make -C /home/thetorpedodog/linux-restricted-modules-2.6.20-2.6.20.5/debian/build/$i/ltmodem \
                        KERNEL_DIR=/usr/src/linux-headers-$i module; \
        done
make: *** /home/thetorpedodog/linux-restricted-modules-2.6.20-2.6.20.5/debian/build/2.6.20-15-386/ltmodem: No such file or directory.  Stop.
make: *** [build-stamp] Error 2
```
I have all my headers and source installed.

Thanks in advance for the help :)

---

