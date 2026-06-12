---
title: "Recompiling the kernel with the &quot;stock&quot; name"
date: 2007-10-27
forum: General Help
---

### Post by samosamo on 2007-10-27
My question is, will recompiling the kernel with the exact stock name 2.6.22-14-generic be any easier than using my own revision name?  Will it cause any damage?

Say I want to recompile my kernel to use SLAB instead of SLUB.  One simple change to stock config. I will use the Gutsy 2.6.22 source to do so.  When I build my own custom kernel to say, 2.6.22-withslab things may get a little more complicated when say, installing a package?  Or using Restricted Drivers Manager?  Because packages will be looking for 2.6.22-14-generic, right?  So I wanted to use the stock name.  I will temporarily rename the old one so I will still be able to boot just in case.

All this to get FGLRX working with Gutsy on a laptop with ATi hardware... sigh

---

### Post by geraldm on 2007-10-27
When you are building your kernel, you can choose to name it what you would desire.
The /boot directory can contain many kernels.  Just add the kernel names to the boot loader.
 It is very probably a BAD practice to change the kernel names, and reuse the former name, 
as this can lead to confusion at a later time.

Scripts should be written to stay versatile, and not hard-code specific paths.
When it is desired to reference modules of the current kernel, a script is used that 
obtains the name of the running kernel  Note the backticks:
```

ls /lib/modules/`uname -r`/kernel

```

Gerald

---

### Post by 5-HT on 2007-10-27
> **samosamo said:**
>  My question is, will recompiling the kernel with the exact stock name 2.6.22-14-generic be any easier than using my own revision name?   It's just a simple one field fix for changing the local version. As to installing certain packages, please see below.> **samosamo said:**
>   Will it cause any damage?  That depends on your config, but the only major issue is that if you install any kernel updates from the repos they'll overwrite your custom one.

 > **samosamo said:**
> When I build my own custom kernel to say, 2.6.22-withslab things may get a little more complicated when say, installing a package?  Or using Restricted Drivers Manager? Because packages will be looking for 2.6.22-14-generic, right?  So I wanted to use the stock name.  Modules need to be compiled against a certain kernel. It has nothing to do with the name. If you name your custom kernel after a ubuntu one, yes the restricted modules will install but that doesn't mean they'll necessariy work and if they do work, it doesn't necessarily mean that they'll work properly-- in essence you're tricking the package manager about dependencies. In your case however, you're using the same version and patch sources with only a few config changes ....it might work[/quote]

Your safest bet is to roll your custom uniquely named kernel and compile any required modules against it or just stick with ubuntu sources instead of trying to mix and match. 
cheers,

---

