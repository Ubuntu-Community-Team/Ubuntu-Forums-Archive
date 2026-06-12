---
title: "An old problem-the os can't not shutdown"
date: 2007-05-11
forum: General Help
---

### Post by cooleeryan on 2007-05-11
From 6.06, 6.10 to my current os-feisty fawn, I cannot shut down my computer with any operations. 
The console will stop at the 'Will now powerdown' bit, and then the fan still work, the HD still walk on by, but the power will not be cut down!
With acpi & apic, my laptop works very good. Using some related arguments, such as acpi=off and noacpi, I cannot resolve my problem, neither.
some pal has good idea? Do me a favor?:)

---

### Post by 13u11fr09 on 2007-05-11
there has to be a better solution, but in the meantime you should be able to shutdown by entering the following in a terminal:

```

sudo init 0

```

hope this helps...

---

### Post by palmdoc on 2007-05-21
Same here. Clean install FF on a Pentium 1.7 GHz with 1 Gb Ram, 40 Gb Hardisk, ATI graphics card. Installation was flawless and it detected my home LAN without issue.
However when I Shutdown, it hangs at the Ubuntu Logo. I have to manually turn off the PC>
I am a newbie so please tell me how to troubleshoot.

Cheers

---

