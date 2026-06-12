---
title: "How to re-compile kernel with BTTV support"
date: 2005-10-31
forum: General Help
---

### Post by CrowBoy1960 on 2005-10-31
Hi,

I'm  relatively new at Ubuntu and would like to re-compile the kernel for BTTV support. I dodwnloaded the BTTV driver and tried to compile it but it looks for a build directory as follows:

root@Crows:~/bttv/bttv-0.9.15 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/root/bttv/bttv-0.9.15 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

I see other threads where people have successfully re-compiled the kernel, presumably with Brooktree cards. Any pointers would be appreciated.

Thanks,

Martin.

PS I've just been looking around and as I have 5.04 I should have probably put it in the Hoary section. Oh, well, slowly learning....

---

### Post by tonym on 2005-10-31
Hoary includes bttv as standard.  I got my Nebula Electronics card working with the standard 2.6 kernel.

---

