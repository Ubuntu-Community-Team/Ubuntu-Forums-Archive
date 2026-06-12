---
title: "Compile built-in kernel driver as separate module"
date: 2014-11-30
forum: General Help
---

### Post by ronniepinsky on 2014-11-30
I am using this in the kernel source root:
```

make -j 4 M=scripts

```
Then:
```

make  -j 4 M=sound/soc/intel

```

I can do this on both the computer I used to compile the kernel or on the target system and when trying to insmod the module I get symbol errors in dmesg and:
```

Unknown symbol in module

```

If I make my own Makefile and compile directly in sound/soc/intel I see compilation errors like this:
```

WARNING: 'sst_byt_get_dsp_position' undefined!

```

When I compile the full kernel the module loads fine.  This isn't practical though because I may need to make a few changes to it and kernel compilation takes too long.  What do I need to include or reference to get this to compile properly?

---

### Post by ronniepinsky on 2014-12-01
I wanted to send this back to the top to actually get some help with this.  If it would take too much time to deal with my issue directly, could you point me to the official documentation that deals with this?  Am I going about this the right way, or should I be trying to reduce my kernel compilation time instead?

---

