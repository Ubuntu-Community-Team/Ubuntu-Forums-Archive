---
title: "Need help recompling usb_storage module"
date: 2006-12-11
forum: General Help
---

### Post by cowbean on 2006-12-11
My apologies if this isn't the right place to ask this question.

I'd like to apply a kernel patch mentioned [here]("http://lists-archives.org/linux-usb-users/02867-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html").  It's basically a minor change to a header file that makes it possible to access a Nokia N80 as a typical mass storage device.  I wasn't exactly sure how to patch the file, but I could figure out that the end result was the addition of subsection in the .h file designating the N80 as an "unusual device".

However, I'm unsure how to go about recompiling the module.  It seems that the default Edgy Eft kernel has usb_storage as an loadable module, as I can see it in the results of lsmod.  However I haven't been able to find instructions to recompile just that one module.  Running "make modules" results in trying to build all the modules, and there is some error that causes make to stop before it gets to the usb drivers.

Any help would be greatly appreciated.

---

### Post by 5T5 on 2007-06-04
You could try SymSMB for that.

---

