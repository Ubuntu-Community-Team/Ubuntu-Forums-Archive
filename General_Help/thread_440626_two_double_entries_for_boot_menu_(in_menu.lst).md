---
title: "two double entries for boot menu (in menu.lst)"
date: 2007-05-11
forum: General Help
---

### Post by 0vermind on 2007-05-11
I don't know which one I am suppost to use but I have 4 ubuntu entires in my boot menu or menu.lst.

```

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,8)
kernel		/vmlinuz-2.6.20-15-386 root=UUID=c1f54ad2-bf5e-4d3c-83c1-3a60ece174fe ro quiet splash
initrd		/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,8)
kernel		/vmlinuz-2.6.20-15-386 root=UUID=c1f54ad2-bf5e-4d3c-83c1-3a60ece174fe ro single
initrd		/initrd.img-2.6.20-15-386


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,8)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=c1f54ad2-bf5e-4d3c-83c1-3a60ece174fe ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,8)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=c1f54ad2-bf5e-4d3c-83c1-3a60ece174fe ro single
initrd		/initrd.img-2.6.20-15-generic

```

so there is Generic, Generic Recovery, 386, and 386 recovery.
as far as I know they all work but which one do I use and why do I have double entires?

Thanks,
Michael - 0vermind

---

### Post by phiphedog on 2007-05-11
You have 2 different kernels on your system. One is generic which has generic settings that will work on the majority of computers. The other one is set to run on and i386 IBM clone. The other 2 options you have are recovery modes for both of these kernels. You'd be best to run the i386 as it will be optimised for your PC and you may get better performance than the generic one but really it doesn't matter if they both work.

---

### Post by m.musashi on 2007-05-11
If you are using edgy or feisty (and I think the 2.6.20-15 kernel is feisty) then you want to use the generic one. They moved away from cpu specific kernels and everything I've read says the generic is the best and will be automatically optimized for your cpu. I have a dual core and the generic works perfectly - dual cores and all.

---

