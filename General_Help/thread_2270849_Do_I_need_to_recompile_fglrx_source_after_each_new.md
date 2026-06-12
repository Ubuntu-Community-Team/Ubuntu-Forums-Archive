---
title: "Do I need to recompile fglrx source after each new kernel install?"
date: 2015-03-26
forum: General Help
---

### Post by hondaman on 2015-03-26
I compile the beta video driver from AMD's website.  Do I need to recompile it every time a new kernel is installed?

---

### Post by bardo2 on 2015-03-26
It's been a while since i used fglrx myself (also beta at times). usually, the recommended way is to use dkms. If you see the output for```
dkms status
```containing a reference to your fglrx driver/version for the current kernel, it will automatically be built when a new kernel release is coming. If not, then not. Easy as that. :-)

---

