---
title: "fglrx 8.6"
date: 2008-06-25
forum: General Help
---

### Post by soxs on 2008-06-25
Ok, I tried latest fglrx (at this time 8.6) and I just wanted to point out one usefull info to get rid of libgl not found (only tested for latest kernel and AMD64):

A. creating the packages (and theoretical installing them):
```
sh ./ati....sh --buildandinstallpkg
```
B. In case you got no red [COLOR="Red"][fail][/COLOR] messages, you're done.
[COLOR="YellowGreen"]**In case B you did get an error about missing libGL.so.1 do:**[/COLOR]
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```
Now run the package installation again
```
cd /where/the\ installer/is
```
```
 sudo dpkg -i xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb fglrx-kernel-source_8.501-0ubuntu1_amd64.deb fglrx-amdcccle_8.501-0ubuntu1_amd64.deb
```

Note: if you get any nasty errors about duplicate fglrx.ko, I simply purged the fglrxdriver directory and started the whole process over again.
_**[COLOR="Red"]Note: This may harm your system, but it worked fine for me. Do it at your won risk:[/COLOR]**_
```
sudo -rm -Rvf /var/lib/dkms/fglrx/*
```

---

### Post by jlward4th on 2008-07-04
Thanks for posting this.  However I get an error with kernel 2.6.26-2-generic while trying to compile the kernel module:
```
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.26-2-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.501/bu
ild/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-2-generic'
  CC [M]  /var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: In function ‘__ke_printk’:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:1980: warning: format not a string literal and no format arguments
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: In function ‘__ke_get_ke_pte’:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2610: error: ‘NOPAGE_SIGBUS’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2610: error: (Each undeclared identifier is reported only once
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2610: error: for each function it appears in.)
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: In function ‘__ke_get_vm_phys_addr’:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2638: error: ‘NOPAGE_SIGBUS’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: In function ‘__ke_get_vm_page_table’:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2660: error: ‘NOPAGE_SIGBUS’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: In function ‘KCL_TestAndClearPageDirtyFlag’:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:2788: error: ‘NOPAGE_SIGBUS’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c: At top level:
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3833: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3833: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3851: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3851: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3858: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3858: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3865: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3865: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3872: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3872: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3879: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3879: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3886: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3886: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3895: error: unknown field ‘nopage’ specified in initializer
/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.c:3895: warning: initialization from incompatible pointer type
make[2]: *** [/var/lib/dkms/fglrx/8.501/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.501/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-2-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Any ideas?  Thanks.

-James

---

### Post by soxs on 2008-07-04
2.6.26? it won't compile without dirty hacks (I  don't know how to fix it). The kernel is just to new. fedora 9 kernel isn't supported aswell, yet.
Edit:9 (sulphur) not 8

---

### Post by ggodfrey on 2008-07-09
Just in case someone else finds this thread.  I got this working using this:

[http://phoronix.com/forums/archive/index.php/t-11049.html]("http://phoronix.com/forums/archive/index.php/t-11049.html")

Gary

---

### Post by soxs on 2008-07-09
I got around that this was allready known before I actually posted *g*
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by mzembe on 2008-07-21
I'm also having trouble with fglrx&2.6.26 - I get that undeclared NOPAGE_SIGBUS problem with the 8.6 ati driver. Is it really an issue with the kernel or fglrx? 
Usually when I get a build error (and then Google it), I can never be sure that maybe I'm only finding other people with the same missing headers.. or something similar. :)

---

### Post by soxs on 2008-07-21
> **mzembe said:**
> I'm also having trouble with fglrx&2.6.26 - I get that undeclared NOPAGE_SIGBUS problem with the 8.6 ati driver. Is it really an issue with the kernel or fglrx? 
Usually when I get a build error (and then Google it), I can never be sure that maybe I'm only finding other people with the same missing headers.. or something similar. :)

It's caused by the fact that fglrx is closed source.
You will have to wait for 8.7 or google some more, I can't help you there (Though it shouldn't take that long anymore untill 8.7 gets released...).

---

### Post by mzembe on 2008-08-07
There is now an 8.7 ati driver, but it doesn't help... and they have the rt patches out for 2.6.26 also. 
I've managed to get a 2.6.26-rt1 kernel working with the 8.6 driver, and I still have everything bookmarked/freshly remembered - so here goes:
I had to stick with the initial 2.6.26 release and the [rt patch]("http://kernel.org/pub/linux/kernel/projects/rt/patch-2.6.26-rt1.bz2") (for those interested, but it complicates things). I configured the kernel like is outlined in [this Gentoo howto]("http://gentoo-wiki.com/HOWTO_ATI_Drivers"), paying special attention to the editing of /usr/src/linux/kernel/rcupreempt.c there near the bottom (only necessary for the rt variants). 
The patch I used for the ati installer is [here]("http://patches.ubuntu.com/by-release/extracted/ubuntu/f/fglrx-installer/2:8.501-0ubuntu3/02_2.6.26_support.patch")- to install the patch I stopped X with the ```
sudo /etc/init.d/gdm stop
``` (gdm=kdm for kde users) and began the installation ala ./ati-driver-installer-8-7-x86.x86_64.run which unpacks everything to a temporary directory. Just switch to another console and change into that temporary directory while the installer is waiting for input on the other console and create a symbolic link to the 'install' directory called 'fglrx-installer-8.501' 
```
>..../fglrx-install.randomsequence# ln -s install fglrx-installer-8.501
``` before patching then ```
cat location/02_2.6.26_support.patch|patch -p0
``` to fix the firegl_public.c. Switch back to the waiting installer and hit 'enter' until is says you're done. One important detail - make sure you turn on [Kernel Hacking -> Enable unused/obsolete exported symbols (UNUSED_SYMBOLS)]("http://forums.gentoo.org/viewtopic-t-696111-postdays-0-postorder-asc-start-25.html?sid=6c7cddcefa6de975ed0d4cfdcc941d4a") or it will fail.

---

