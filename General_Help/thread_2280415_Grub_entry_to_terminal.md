---
title: "Grub entry to terminal"
date: 2015-05-30
forum: General Help
---

### Post by newb85 on 2015-05-30
Is there a way to create a GRUB entry that leads directly to a terminal, bypassing xorg?  I know recovery console takes you to a root terminal.  I just want to go to a regular terminal.

---

### Post by oldfred on 2015-05-31
I have seen this which changes all entries.

 Uncomment #GRUB_TERMINAL=console from /etc/default/grub

I think you could add boot parameter as I have seen posts with that, but do not remember nor saved instructions.

---

### Post by v3.xx on 2015-05-31
A couple of additional steps here, if need apply.

[http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

---

### Post by newb85 on 2015-06-01
Yes, I've seen those.  But I don't want to make all my grub entries go to TTY.  I want a new entry that leads to TTY.  I want my old entries to remain in tact, leading to the GUI.

For that matter, I would be satisfied with simple instructions for manually entering the option into GRUB each time I boot, rather than changing GRUB's settings at all.

---

### Post by oldfred on 2015-06-01
See v3.XX link.
Each of those grub changes are the commands it is adding after or in place of the quiet splash.

So just during boot use e on grub menu, and replace quiet splash with text, not sure if in grub you have to edit the GRUB_TERMINAL=console in addition or if that is just another permanent setting.

---

