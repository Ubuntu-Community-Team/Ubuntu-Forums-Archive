---
title: "Where are kernel modules stored?"
date: 2007-07-30
forum: General Help
---

### Post by weblordpepe on 2007-07-30
Hello fellow Ubuntu boys & girls.

I understand that the linux kernel ships with all device drivers for all the hardware in the universe. These are files, (.ko files I think?)

My question is, where are these files? So I can modprobe them and rmmod them. Basically I'd like to know where all the drivers are for my linux system. It'd be nice to build some kind of GUI to browse them eventually.

---

### Post by 5-HT on 2007-07-30
Modules for each kernel are stored under their own directory in /lib/modules/.
There's no need to know the patch to insert/remove them from the kernel though, just the name will suffice.
cheers,

---

### Post by weblordpepe on 2007-07-31
HmmMmMmMmmmm
Cool thanks very much :)
Does modprobe just magically find the files it needs by doing a search in that directory?

---

### Post by 5-HT on 2007-07-31
Yup :). The modules are compiled against a specific kernel, which is why there are modules for each of your kernels in /lib/modules and why you only need to specify the name for modprobe. If the modules name is foo.ko, simply issuing a 'modprobe foo' will do the trick.
You can see a list of the available modules for a kernel by issuing a 'modprobe -l' and see a list of your loaded modules with 'lsmod'.
cheers,

---

### Post by weblordpepe on 2007-07-31
weeeeeeeee!!

thanks :D

---

