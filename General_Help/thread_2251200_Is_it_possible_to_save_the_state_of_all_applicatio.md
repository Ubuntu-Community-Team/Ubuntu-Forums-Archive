---
title: "Is it possible to save the state of all applications before shutting down?"
date: 2014-11-02
forum: General Help
---

### Post by blackbird34 on 2014-11-02
Hi all, 

I'm currently running a dual boot Windows 8.1 / Ubuntu 14.04. Everything is rosy. Haven"t used Windows for a month :) 
On my previous computer I ran XFCE, it had an option to save the state of all applications (whatever documents they were editing, etc) on logout. It was useful in theory (but the Celeron i had couldn't handle the extra load on startup wery well, so i didn't use it much.)

Can Unity  save the state of all open applications and restart them all as they were after a reboot? Would there be any way to do this? I can't hibernate (set up a swap partition that was too small and in an awkward place on the drive), and i'm thinking of use cases when i'd shut down Ubuntu, boot into Windows and then come back.

Is this possible? Any workarounds?

Thanks in advance,

---

### Post by tgalati4 on 2014-11-03
One work around is to create a swap file such that your swap partition plus your swap file exceeds your RAM size.  When you reboot, use

```
free
```

to determine that both swap spaces are being detected and used.  Then try hibernating a few times with some applications and files open.  Make sure it is reliable.  Yes, hibernation is as slow as a cold boot, so I don't use it either.

You will have to search how to create the special swap file:

```
man mkswap
man swapon
```

---

