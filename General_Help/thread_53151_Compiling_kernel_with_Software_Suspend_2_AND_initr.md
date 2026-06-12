---
title: "Compiling kernel with Software Suspend 2 AND initrd"
date: 2005-07-30
forum: General Help
---

### Post by pr00f 0f d3f on 2005-07-30
In a [previous post](http://ubuntuforums.org/showthread.php?t=51922), I had compiled Software Suspend 2 with a vanilla kernel, in hopes of getting hibernation (or any type of power management) working with my Dell Inspiron 1000. Instead, i got a kernel panic. My conclusion is that this was because initrd was not compiled in. So, here is my dilemma:

Without initrd, ubuntu won't start.

Initrd won't compile on the vanilla kernel, because of the cramfs bug.

I can't find an Initrd cramfs patch, and the only kernel i found that has it is the debian/ubuntu one.

Software suspend 2 won't patch onto a debian kernel.

Any suggestions? comments? screams of terror?  ](*,)  I'd really like to get this working, so i don't have to shutdown my laptop every time i go somewhere.

---

### Post by pr00f 0f d3f on 2005-07-31
[QUOTE=pr00f 0f d3f]In a [previous post](http://ubuntuforums.org/showthread.php?t=51922), I had compiled Software Suspend 2 with a vanilla kernel, in hopes of getting hibernation (or any type of power management) working with my Dell Inspiron 1000. Instead, i got a kernel panic. My conclusion is that this was because initrd was not compiled in. So, here is my dilemma:

Without initrd, ubuntu won't start.

Initrd won't compile on the vanilla kernel, because of the cramfs bug.

I can't find an Initrd cramfs patch, and the only kernel i found that has it is the debian/ubuntu one.

Software suspend 2 won't patch onto a debian kernel.

Any suggestions? comments? screams of terror?  ](*,)  I'd really like to get this working, so i don't have to shutdown my laptop every time i go somewhere.[/QUOTE]
 so, uh, doesn't work today either. in case that's what you were all implying by completing ignoring the thread ;)

---

### Post by i3dmaster on 2005-08-11
[QUOTE=pr00f 0f d3f]so, uh, doesn't work today either. in case that's what you were all implying by completing ignoring the thread ;)[/QUOTE]
man you got my sympathy. I had exactly the same situation as you had. Still searching around but this seems an extremely difficult issue to get resolved.

---

