---
title: "Ubuntu 8.04 Beta Wubi problem"
date: 2008-03-21
forum: General Help
---

### Post by oasmar1 on 2008-03-21
hi, i installed the new beta today with wubi and everything was going well stright after installation. then it came up in the corner that i needed to install some properitatry drivers for ati, i did this and rebooted. 
Now when the computer boots, it goes to the:

              ubuntu
[||||||||||||||||||||---------]

boot screen then goes black after this.
it does not say "no signal" on my monitor so i can only assume its something wrong with the drivers. What can i do to fix this? 
(I found that ubuntu 8.04 is the best ubuntu (and linux) i have ever used, also im not a pro with linux, just a simple user)

Edit;
Here are my system specs:
AMD 3000+
Biostar Motherboard (k8VGA)
Ati x1650Pro AGP.

---

### Post by justleen on 2008-03-21
go into a terminal by pressing ctrl-alt-F2
in there, stop gnome first
```
 sudo /etc/init.d/gdm stop

```
then reconfigure X (make sure to select the vesa driver! most option can just be left default)
```
 sudo dpkg-reconfigure xserver-xorg
```
restart X (same command, but with start), and you should have a non-ati X again

---

### Post by oasmar1 on 2008-03-21
I tried to do what u said but I couldn't because I can't do the ctrl-alt-f2 thing as the screen goes black and even if I press it I can't do anything as the screen stays black.

---

### Post by justleen on 2008-03-21
can you try to boot into recovery mode (from the grub menu)?

---

