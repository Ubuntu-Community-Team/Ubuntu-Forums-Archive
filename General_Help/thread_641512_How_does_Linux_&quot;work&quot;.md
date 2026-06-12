---
title: "How does Linux &quot;work&quot;?"
date: 2007-12-15
forum: General Help
---

### Post by NoOne2 on 2007-12-15
I've asked this question before and tried to find some info on the subject but no real luck.

I've been a Windows user for years and an old pre-OSx Mac user.

When I had a problem I was able to troubleshoot it because I knew how the system worked.  I understood the relationship between the OS and applications and more importantly how the driver model worked in both OS's.

Linux is totally different.  I fail to understand the relationship between drivers and the kernel.  What recompiling the kernel really means.  I know what it is "mechanically" but why is this done versus the model used on other OS's.

I run into a lot of frustrating road blocks and there are a lot of great answers here but they are "do this" not "this is why you want to do this".  I don't want to know how to fix them, I want to understand why they are broke.

I lose a lot in reading directions because if there is a problem I can't follow the logic of what is supposed to be happening.

I've tried books but they seem to skip this very fundamental step.

Understanding how dependencies really work would be a big help.  I know one package is reliant on another but what is the process to find all that out instead of playing install one package and see which one is needed next.

Any good reading someone can recommend?  I'm missing that one link that will put this together in my head.

My understanding is a bit better than I've stated but I don't want to miss anything so ground up is best.  
Thanks

---

### Post by SunnyRabbiera on 2007-12-15
well basically linux itself is a kernel not a operating system as its traditionally defined.
what you see when you log into linux is shells wrapped around it but they are kept separately from the main core.
basically what they mean by recompiling the kernel is that people are allowed to modify and redistribute the linux core as their own, this is all due to linux not being like most other operating systems by allowing people to make modifications to their systems free of charge...
if you dont like how your system works you can make it work as you wish if you had the knowhow

---

### Post by sirdilznik on 2007-12-15
Recompiling the kernel means that you get to go right into the heart of your system and change settings and options.  The generic kernel that comes with Ubuntu by default has most things built as modules.  Only needed modules are loaded by your system (or ones you specifically tell it to).  If you know your hardware inside and out then you can select only options for your very specific hardware (either as modules or built directly in) streamlining the kernel and making it smaller.  You can also add patches to the kernel to expand functionality.

One specific advantage this has over say a Windows system is that the Windows kernel has a whole bunch of services on all the time by default.  This makes things easy and plug n play, but it also leaves many security holes (every additional service running is another potential exploit).  In Linux you can strip out all unnecessary services right at the kernel level meaning they can never run and thus can't be exploited.

---

### Post by NoOne2 on 2007-12-15
ok to simplify parts of what you said.

When I first run the installer I get the very very basic kernel.

When it does hardware detection and all that certain modules are integrated into the kernel, correct?

There are no "drivers" like in Windows that operate under a separate piece that loads, they become integrated at what would be considered ring 0 in Windows?

---

