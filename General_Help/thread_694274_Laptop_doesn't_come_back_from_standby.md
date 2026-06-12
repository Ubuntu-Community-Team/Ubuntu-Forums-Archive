---
title: "Laptop doesn't come back from standby"
date: 2008-02-11
forum: General Help
---

### Post by s0n|k on 2008-02-11
f i shut the lid or put the laptop into standby, the wireless/battery/power lights remain lit. It doesn't do that with Vista... How can I make it fully go into standby? Also, when I raise the lid I usually have to POR the machine. It rarely comes back from being in standby. Anyone else have these problems? I have a Sony Vaio CR320E with Gutsy.

---

### Post by Het Irv on 2008-02-14
I have a hp Compaq 672Ds (everything works OOB except Compiz Graphics, and that works with a couple lines of code).

But I have that same problem, I don't know of any solution.

---

### Post by jpittack on 2008-02-14
Please provide your graphics card type, and the driver that you are using for it.

---

### Post by Het Irv on 2008-02-14
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Sorry, but I don't remember what I did exactly to get compiz to work.  I know the code basically told Compiz/Ubuntu to not check for compatibility and go ahead and run the desktop effects.

---

### Post by Thingymebob on 2008-02-14
Same issue here with my Acer Aspire 5103 (ATI Radeon Mobility X1300)

---

### Post by jpittack on 2008-02-14
For ATI users, using the fglrx driver in the repos (8.37), you will not have suspend and hibernate.  The issue is that the fglrx driver doesn't work with the new slub allocator that is in kernel 2.6.21 and above.  The new driver (7.12 and above) work with kernels 2.6.23 and above.  You are more then welcome to try the new drivers.  If they don't work, and you still want to try more, recompile the kernel to not include the new slub allocator, or use a newer kernel with the latest fglrx.

As an ATI user, I am using the default driver, and have full functionaly, and 3D support.  Because I don't have aiglx support, and xgl will rob my battery life, I don't use compiz.

So for ati users, your choices are
use default drivers
compile kernel with manual install of fglrx
compile same kernel with same drivers, which are less buggy
wait for hardy

For intel, you have the blacklisted driver for running compiz, as you found out.
Intel may have a different driver for you to try.  There is a stable one and an experimental one.  I do not know the names for them.

There are tons of threads already started about these subjects.  I suggest trying those.  More input can be found there.

As for dropping the lid to have the computer enter standby, you can change the settings in System > Preferences > Power Management.  Until your computer will return from suspend, don't enable this.

---

