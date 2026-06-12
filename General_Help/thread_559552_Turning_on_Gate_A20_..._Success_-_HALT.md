---
title: "Turning on Gate A20 ... Success - HALT"
date: 2007-09-25
forum: General Help
---

### Post by kjma on 2007-09-25
Hi again

I wanted to install wubi on my workstation as well, but when i try to boot i get:

```

(hd0,0)
Filesystem type is NTFS, partition type 0X7
Turning on Gate A20 ... success


```

After that nothing happens anymore, and if i wait too long with a reset the computer dont wanna boot at all for some minutes. Very strange isnt it? Any idea what could cause this mysterious error?

---

### Post by tinybit on 2007-09-25
Just at startup, press the INSERT key as soon as possible, and you will be able to trace the boot process step-by-step. Post the debug info please.

---

### Post by kjma on 2007-09-25
Well its  not that important cause i planed to get me a 'normal' ubuntu as soon as possible i can afford me CDRs again. I just thought maybe someone had the same problem and give me a tip how to fix this. 

I try to get some debug infos maybe later, but the fact that the PC dont boot for some minutes after the halt is annoying.

---

### Post by kjma on 2007-09-25
Allright,

it says int13/02(80),err=0, failure

---

### Post by tinybit on 2007-09-25
That should not be the only message. Please post all messages displayed.

PS: can you enter the grub command line by pressing c at startup?

At the grub prompt, type the following commands:

debug 0x7FFFFFFF
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (fd0)

and post the output.

---

