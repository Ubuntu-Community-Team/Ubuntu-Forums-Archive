---
title: "kernel booting problems after building a new kernel"
date: 2007-12-04
forum: General Help
---

### Post by ragas on 2007-12-04
I compiled and built a kernel (2.6.16) with some custom configurations. But it does not boot. When I checked using the recovery mode, I see the following lines: 

```
...
...
[17179578.56000] [<c01d4cea>] rb_insert_color+0xaa/0xe0
[17179578.56000] [<c0155637>] vma_link+0x77/0xf0
[17179578.56000] [<c01563a4>] do_mmap_pgoff+0x554/0x750
[17179578.56000] [<c01080a6>] sys_mmap2+0x56/0x8e
[17179578.56000] [<c0102f59 >] syscall_call+0x7/0xb
[17179578.56000] Code: 3b 1d e8 17 34 .... 
                                    .... 
[17179578.56000]
```

It just halts after these lines. Nothing happens. How do I go about debugging this problem?

---

