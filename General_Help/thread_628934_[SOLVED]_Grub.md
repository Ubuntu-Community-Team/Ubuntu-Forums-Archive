---
title: "[SOLVED] Grub"
date: 2007-12-01
forum: General Help
---

### Post by dstein on 2007-12-01
In my GRUB Menu, I first have a listing for my Windows XP installation. My Ubuntu options are listed afterwards. There are so many choices, such as:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)

and the list continues...

I only ever use the top one, which has the newest kernel. Is there any reason that so many options are necessary. What should I edit in menu.lst such that the automagic kernel list only lists two Ubuntu's, the newest one and the newest one in recovery mode? Is this a bad idea?

Thanks.

---

### Post by LaRoza on 2007-12-01
To remove (hide) the older kernels, comment out their entries in grub.

```

gksudo gedit /boot/grub/menu.lst

```

Comment out (place a "#" in front of" the entries you don't want.

---

### Post by wjp.reg on 2007-12-01
Or you can remove the kernel versions you don't want in synaptic and have grub rewritten automatically.

---

### Post by dstein on 2007-12-01
Is there anyway to have this done as a more automatic process, rather than commenting out myself or removing those Kernels? For example, is there an option I can set in menu.lst so that only the most recent version is displayed in GRUB? Thanks.

---

### Post by meierfra on 2007-12-01
Sure, 

For example if you change 

"#howmany=all" (in menu.lst) to "#howmany=3"   you will have  three  sets of kernels on your grub menu.  Each set  gives the two  entries, the regular mode and recovery mode.

So you  probably  want to  use "#howmany=1"

Then type "sudo update-grub" in a terminal  to make the change effective.

---

