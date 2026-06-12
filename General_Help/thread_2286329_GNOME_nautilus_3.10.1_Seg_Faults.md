---
title: "GNOME nautilus 3.10.1 Seg Faults"
date: 2015-07-11
forum: General Help
---

### Post by nbulischeck on 2015-07-11
Has anyone figured out how to fix this? I've been using Krusader for the time being and it's ok, but nautilus <3.

The only thing I get when running it is Segmentation fault (core dumped).

Even as root.

 ```
root@computer:~# nautilus
Segmentation fault (core dumped)
root@computer:~#
```

Is there any way to fix this? All I can find are bug reports. I saw on the arch forum that they downgraded sqlite. Does that have any effect for us?

---

### Post by dragonfly41 on 2015-07-12
I suggest that you first install **gdb** (debugging package) from Ubuntu Software Centre.

Next .. in command line .. enable core files:** $ ulimit -c unlimited**

Then follow tips as in here .. [http://unix.stackexchange.com/questions/132192/running-application-ends-with-segmentation-fault](http://unix.stackexchange.com/questions/132192/running-application-ends-with-segmentation-fault)

e.g .. **sudo gdb krusader**

---

### Post by nbulischeck on 2015-07-12
```
Program received signal SIGSEGV, Segmentation fault.
0x00007fffd5d0d23e in PyErr_GivenExceptionMatches ()
   from /usr/lib/x86_64-linux-gnu/libpython2.7.so.1.0
(gdb) bt
#0  0x00007fffd5d0d23e in PyErr_GivenExceptionMatches ()
   from /usr/lib/x86_64-linux-gnu/libpython2.7.so.1.0
#1  0x00007fffd5cb9bdf in PyErr_PrintEx ()
   from /usr/lib/x86_64-linux-gnu/libpython2.7.so.1.0
#2  0x00007fffd671a7e4 in ?? ()
   from /usr/lib/nautilus/extensions-3.0/libnautilus-python.so
#3  0x00007fffd671af63 in nautilus_module_initialize ()
   from /usr/lib/nautilus/extensions-3.0/libnautilus-python.so
#4  0x00000000004c9946 in ?? ()
#5  0x00007ffff491f0a1 in g_type_module_use ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#6  0x00000000004c9bb1 in ?? ()
#7  0x000000000042cddb in ?? ()
#8  0x00007ffff48fb5e7 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#9  0x00007ffff4914088 in g_signal_emit_valist ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#10 0x00007ffff4914ce2 in g_signal_emit ()
   from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#11 0x00007ffff4bde06a in g_application_register ()
   from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#12 0x000000000042c89e in ?? ()
#13 0x00007ffff4bdeacb in g_application_run ()
   from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#14 0x000000000042b561 in ?? ()
#15 0x00007ffff3b00ec5 in __libc_start_main (main=0x42b4a0, argc=1, 
    argv=0x7fffffffe0f8, init=<optimized out>, fini=<optimized out>, 
    rtld_fini=<optimized out>, stack_end=0x7fffffffe0e8) at libc-start.c:287
#16 0x000000000042b5c3 in ?? ()
```

Alright how do I fix this?

Before I did the traceback I got this Traceback (most recent call last):
```

  File "/usr/share/gdb/auto-load/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19-gdb.py", line 63, in <module>
    from libstdcxx.v6.printers import register_libstdcxx_printers
ImportError: No module named 'libstdcxx'

```

So I try to install libstdc++ and I get a tonn of conflicting errors.

---

### Post by dino99 on 2015-07-12
using nautilus on a kde system is not expected (and has not been tested) as its a gnome app

---

### Post by nbulischeck on 2015-07-12
I'm on gnome 3 though lmao

---

