---
title: "Possible to get old oss modules without compiling entire kernel ?"
date: 2012-11-05
forum: General Help
---

### Post by interzoneuk on 2012-11-05
Hi.

At present I need the oss modules (some old games I play require them at present...).

I can compile a kernel no problem (presently running one with the snd-pcm-oss + snd-seq-oss modules (and changed to run at 1000Hz frequency...) using a combination of the instructions 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)  and [http://blog.avirtualhome.com/compile-linux-kernel-3-2-for-ubuntu-11-10/](http://blog.avirtualhome.com/compile-linux-kernel-3-2-for-ubuntu-11-10/)  (I use the linux-source package - I make a .i5 varient..) 

Rather than have to compile an entire kernel is it possible to just compile the missing oss modules from the kernel headers package?

I came across this - [http://lxr.linux.no/#linux+v2.6.28.3/Documentation/kbuild/modules.txt](http://lxr.linux.no/#linux+v2.6.28.3/Documentation/kbuild/modules.txt) but that didn't excatly make sense.

Is there an easy way to add the modules  (I am happy to compile the kernel but seeing as I am just essentially adding the 2 missing oss modules I thought it may be 'overkill'

---

