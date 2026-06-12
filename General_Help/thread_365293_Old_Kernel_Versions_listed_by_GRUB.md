---
title: "Old Kernel Versions listed by GRUB"
date: 2007-02-19
forum: General Help
---

### Post by Raptor45 on 2007-02-19
Pretty easy question I think, and more of an annoyance than anything.

After Ubuntu updates to a new kernel, grub lists the old ones as well as the latest This gets especially annoying after several updates have gone by. Is there any way to get rid of these listings? How about keeping them from showing up in the future?

---

### Post by konst88 on 2007-02-19
You need to remove them using synaptic or aptitude.
Just search for the name linux, and check the version number.

---

### Post by Raptor45 on 2007-02-19
Thanks that did the trick. Is there any reason this has to be done manually though? I can't imagine most users have a need for multiple versions, and having to do this every time I worry at some point I'll click the wrong ones.

---

### Post by Ramses de Norre on 2007-02-19
What if the new kernel doesn't work? You'll end up with an unbootable system... 
So I think it's quite good that the old kernels remain on your system.

---

### Post by Raptor45 on 2007-02-19
What if it were to check after the reboot to see if everything went ok, and not remove it until then? This could include having an option for a popup asking "Would you like to remove outdated kernels? y/n"

EDIT: Its not really a problem, and may be desirable from a tech-user standpoint, but from a noob-user standpoint I think it could be confusing/annoying.

---

### Post by Xappe on 2007-02-19
I think there is a way to tell grub to show only a few of the kernel entries in the menu (though  the kernels are still there if you need them). Have to look into it further though...check the manual pages for grub in the meantime :)

---

### Post by Patrick K on 2007-02-19
Edit /boot/grub/memu.lst and put a "#" in front of the ones you want to hide.

---

### Post by Xappe on 2007-02-19
look for the line

#howmany=all

in your menu.lst. 

Don't uncomment it, but change "all" to the number of kernels you would like to show in the menu, for example:

#howmany=3

then run

sudo update-grub

---

### Post by A. J. Rimmer on 2007-02-19
After removing unneeded kernels with Synaptic, run "sudo update-grub" to generated a new menu.lst.  See "info update-grub" for details.

---

