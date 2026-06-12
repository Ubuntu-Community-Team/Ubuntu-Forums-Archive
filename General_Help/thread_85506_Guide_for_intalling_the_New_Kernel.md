---
title: "Guide for intalling the New Kernel"
date: 2005-11-02
forum: General Help
---

### Post by Drifter on 2005-11-02
Does anyone know where a good guide that explains how to install the new kernel can be found.  I used one two or three times but got no where with it.

---

### Post by RAOF on 2005-11-02
Have you tried [this guide]("https://wiki.ubuntu.com/KernelHowto")?  You can replace the "obtaining the source" bit by just downloading the kernel.org kernel source.  Under "configuring the kernel", I suggest replacing those steps with
```

make oldconfig
make gconfig

```
The first will copy the configuration from the running kernel, which is good.  The second will allow you to change any of the kernel options you want.

Then follow the guide.  It worked for me :)

---

### Post by Drifter on 2005-11-02
Sorry I have been away for awhile.  Yes I tried that guide and another one in the forum.  I know I am doing something wrong myselve but I don't know what.  The first time i tried I got all the way through, but the new kernel did not show up.  That was with the other guide.  Then I tried again with the same guide and got error messages and could not continue with the process.make[3]: *** [drivers/net/eepro.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2
I tried the other guide that u pointed to but could not get to far with it.  I like ubuntu and I am not discouraged because I figure that experimenting with thing will help me in the long run.  But I would like to be able to do this.  Any help would be appreciated.

---

### Post by ecobuntu on 2005-11-02
try this
[http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)

This is specifically for 2.6.14...

---

### Post by Drifter on 2005-11-03
5-Let's build the kernel:

*In a terminal make sure you are in /usr/src/linux with full root access.

We will build a ".deb" file that can be installed in our Ubuntu system, using make-kpkg.

*In a terminal type:

Code:

make-kpkg clean make-kpkg -initrd --revision=ck1 kernel_image


If there wasn't errors this will build the kernel and a ".deb" file will be created at /usr/src.
When I get to nol.5 this is what happens the errors, what am I doing wrongmm/mmap.c: In function ‘copy_vma’:
mm/mmap.c:2009: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [mm/mmap.o] Error 1
make[1]: *** [mm] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

---

### Post by JogerNaut on 2005-11-03
You need fakeroot when you use make-kpkg. So instead of make-kpkg clean you need to run fakeroot make-kpkg clean and fakeroot make-kpkg --append-to-version="*appendtoversion*" --revision=... etc..etc..

---

### Post by RAOF on 2005-11-03
No idea.  Some part of the kernel code isn't compiling correctly, and so nothing is being built.

Let's try from the beginning:
[LIST]
[*]sudo adduser <your_username> src
[*]su <your_username>
[*]Download the linux source from kernel.org
[*]cd /usr/src
[*]sudo rm -r * **make sure you are in the /usr/src directory.  This can kill your system if you're in the wrong directory**
[*]cp /path/to/linux-2.6.14.tar.bz2 .
[*]ln -s linux-2.6.14 linux
[*]cd linux
[*]cp /boot/config-$(uname -r) .config
[*]make gconfig
[*]make-kpkg --append-to-version=<whatever> --initrd --rootcmd fakeroot buildpackage
[*]cd ..
[*]sudo dpkg -i <whatever deb got built>.deb
[/LIST]

---

### Post by Drifter on 2005-11-03
root@ubuntudlt:/usr/src/linux# fakeroot make-kpkp clean
/usr/bin/fakeroot: line 150: make-kpkp: command not found
root@ubuntudlt:/usr/src/linux# make-kpkg fakeroot make-kpkg clean
Error: Unknown target fakeroot Unknown target make-kpkg
use --targets to display help on valid targets.
root@ubuntudlt:/usr/src/linux#

This is what i get when I try what u said to do.  I may not understand what you are saying, explain in more detail please.

---

### Post by JogerNaut on 2005-11-03
From your post it seems you're logged in as root so you don't need to use fakeroot. As RAOF said, you're running into errors when you try to compile the kernel. Try to start from the beginning using RAOF's instruction.

---

### Post by Drifter on 2005-11-03
I haven't had time to try again, but after work today I will try and let u know.  Thanks for the information stay tuned I am not going to give up on this because this is how u learn.

---

### Post by tonysathre on 2005-11-03
i think u can install new kernels from synaptic

---

### Post by Drifter on 2005-11-03
Could u explain how this is done.  I am very new and would like to know how to do this.  Thanks

---

### Post by tonysathre on 2005-11-03
open synaptic and search for kernel, check it, and hit apply

---

