---
title: "Recompiling kernel errors (real-time)"
date: 2008-07-01
forum: General Help
---

### Post by TuxBobble on 2008-07-01
I'm trying to compile a patched version of Linux kernel 2.6.25.8 with a real-time patch.  I ran make menuconfig to mess with my conifguration as needed, but whenever I use the make all command afterwards I get the following error:

```
mm/slub.c: In function ‘slab_unlock’:
mm/slub.c:1172: error: implicit declaration of function ‘__bit_spin_unlock’
make[1]: *** [mm/slub.o] Error 1
make: *** [mm] Error 2
```

Can anyone explain why I'm getting this code, if they understand it?

Additionally, if anyone can help me out, another thing I'm trying to figure out is how to load the Linux kernel alone (i.e. not Ubuntu or any other distribution) onto a new computer that does not currently run Windows/Linux/etc.  It currently runs FreeDOS and will be formatted in the near future, but I can't understand how to make it work properly since I don't have a standard OS installed from which I can install something like GrUB, etc...

---

### Post by TuxBobble on 2008-07-07
Anyone got any ideas?

---

### Post by tthtlc on 2008-07-19
I got the same errors too.

In include/linux/bit_spinlock.h:

      1 #ifndef __LINUX_BIT_SPINLOCK_H
      2 #define __LINUX_BIT_SPINLOCK_H
      3 
      4 #if 0
      5 
      6 /*
      7  *  bit-based spin_lock()
      8  *
      9  * Don't use this unless you really need to: spin_lock() and spin_unlock        ()
     10  * are significantly faster.
     11  */
because of the if 0 above the function is not compiled.

So just extract out the following function and put it outside the ifdef:

     86 static inline void __bit_spin_unlock(int bitnum, unsigned long *addr)
     87 {
     88 #ifdef CONFIG_DEBUG_SPINLOCK
     89         BUG_ON(!test_bit(bitnum, addr));
     90 #endif
     91 #if defined(CONFIG_SMP) || defined(CONFIG_DEBUG_SPINLOCK)
     92         __clear_bit_unlock(bitnum, addr);
     93 #endif
     94         preempt_enable();
     95         __release(bitlock);
     96 }

I relocated it to line 86 above, and all compiled ok.

---

