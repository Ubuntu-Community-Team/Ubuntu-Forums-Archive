---
title: "Rebooting into a different OS - Out of curiosity..."
date: 2007-12-27
forum: General Help
---

### Post by jbysmith on 2007-12-27
This is mostly a "just out of curiosity" thing, wondering if it can be done, and if so, how.  Still learning how things work, and like trying out new things.

I use Gutsy as my primary OS, with a small XP partition that I occasionally boot into for a few games that don't play nicely with Wine.  I also have a virtual machine that gets reformatted when I'm toying around with other distributions, just to see whats out there.

Tried the latest SuSE.  Wasn't for me, but one thing that was kind of a nice touch was the ability to reboot into a different operating system right from the menu.  

Stupid, yes.  Fluff, absolutely.  Can I do it from the GRUB menu, yes.  

Just curious if this can be done with Gnome.  Say on the shutdown screen (the one that gives you shutdown, reboot, suspend etc etc) if you can add an option to reboot into a different partition.

Thanks

---

### Post by nukie77 on 2007-12-27
I suppose you could write a script that replaces the menu.lst of grub with one that boots into your other OS of choice, but then you would also have to have another script on that other OS that would replace menu.lst to its original form, or the system would continue to boot into the second OS.

---

