---
title: "ubuntu kernel sources"
date: 2007-12-31
forum: General Help
---

### Post by arana on 2007-12-31
Hello Everyone.

I have just joined a forum, I am both new to linux and ubuntu. I like to know where kernel sources are installed for unbutu, I have a kernel version 
2.6.22-14. Also if somebody can please let me know if ubuntu is a free bsd/
open bsd or netbsd etc.

And also I will appreciate if somebody can let me know, where kernel config file resides, I need to run 

make depend 
make 
make install

Please let me know...

Kind regards
Zieb Rana

---

### Post by nick_h on 2007-12-31
Ubuntu is a linux based on Debian.

The kernel sources are available in the package linux-source-2.6.22 which will install to /usr/src as a tar.bz2 file.

The current config file can be found in /boot

Have a read of the [Master Kernel ](http://ubuntuforums.org/showthread.php?t=311158) thread.

---

### Post by arana on 2007-12-31
Hi All,

Thanks for replying back. In my /usr/src directory all I have is two directories named:

linux-headers-2.6.22-14, and linux-headers-2.6.22-14-generic.

Please tell me if I need to seperately download sources directory or sources reside in linux-headers-2.6.22-14, and linux-headers-2.6.22-14-generic.

I basically need to run a patch -pl command in the kernel sources directory. 

However running patch -pl at the moment is generating following error:

patch: **** strip count l is not a number.

Please respond back...

Kind regards
Zieb Rana

---

### Post by geirha on 2007-12-31
Then you'll need to install the linux-source-2.6.22 package. linux-headers-* only contain the header files.

---

### Post by nick_h on 2008-01-01
Yes, you will need to install the full kernel source.  Read the link I gave in my first post.

Step 4 suggests that you download the vanilla source from kernel.org - you could always install the Ubuntu source package instead.

Steps 6 and 7 download and apply a patch.  You will need to apply your patch instead.

---

### Post by ~LoKe on 2008-01-01
Err...hold on.  You're new to linux, yes?  What is this patch you're trying to apply, and what is it for?  Are you sure there's no alternative?  I mean, patching a kernel is not the first job I'd give to a beginner...

---

### Post by arana on 2008-01-01
I am trying to put sebek. This is why I need to do patching.

---

### Post by arana on 2008-01-01
I am trying to put sebek. This is why I need to do patching.

Thanks for replies guys...

Kind regards
Zieb Rana

---

