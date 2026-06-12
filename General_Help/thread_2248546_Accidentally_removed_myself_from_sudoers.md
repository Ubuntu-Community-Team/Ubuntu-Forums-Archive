---
title: "Accidentally removed myself from sudoers"
date: 2014-10-15
forum: General Help
---

### Post by Gottier on 2014-10-15
I am using Ubuntu 14.04.
Ubuntu 14.04 is the only operating system.

I accidentally removed myself from sudoers. I was trying to add myself to another group, but didn't use -a. 

I can't access the recovery when booting with shift key held down. It just boots to Ubuntu.

 If I boot from live CD and try to mount sda1 then chroot to it, it tells me bin/bash not found. 

I've looked at too many web pages online that all say the same thing, and I can't get past these points, so now I must ask here. 

If I must re-install Ubuntu then I will, but if anyone can help me I'd appreciate it.

---

### Post by deadflowr on 2014-10-15
At what point do you press the shift key?
(It should be when the screen goes blank after the first bios screen, immediately)

And what commands do you run from the livecd/chroot?

---

### Post by Gottier on 2014-10-15
I have tried it at various points. I've held it down the whole time. I've tried the right one, the left one. Held it down right after first bios screen, before first bios screen, etc, etc.

---

### Post by Bashing-om on 2014-10-15
Gottier; Hello .

EFI system ? Then EFI looks for the escape key rather then the shift key .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Gottier on 2014-10-15
> **Bashing-om said:**
> Gottier; Hello .

EFI system ? Then EFI looks for the escape key rather then the shift key .
[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]


Oh, bless you! This worked, and I was able to add myself back to the default groups (and sudo).

Thank you, thank you, thank you!

---

### Post by Bashing-om on 2014-10-15
Gottier; Outstanding !

Pleased all has worked out.

Please mark this thread solved: top of post -> thread tools.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

