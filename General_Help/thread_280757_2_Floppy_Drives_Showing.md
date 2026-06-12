---
title: "2 Floppy Drives Showing"
date: 2006-10-19
forum: General Help
---

### Post by scottieblues on 2006-10-19
I just installed a fresh copy of Edgy.
Love it!!!

One question...

I only have 1 Floppy Drive.
Why are 2 showing up in my Computer folder?

Thanks in advance for any help.

scott

---

### Post by IronChef69 on 2006-10-20
I have the same problem.  Only happens on my new Core 2 system with p965 chipset motherboard.  I never really looked into it since I was happy enough just getting the jmicron ATA controller working.  I'm a real GNU/Linux noob, but I guess it might be possible to configure the fstab file in such a way to just ignore the extra drive somehow, but I know next to nothing and I'm probably way off.

---

### Post by alexszis on 2006-10-24
I had the same problem here and i solved editing the /etc/fstab file.
The line that mount the floppy drive was this:
```
/dev           /media/floppy0  auto    rw,user,noauto  0       0

```
and i changed to
```
/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0

```
I hope i can help you
and sorry for my bad english

---

