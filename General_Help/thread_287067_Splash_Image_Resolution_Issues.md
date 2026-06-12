---
title: "Splash Image Resolution Issues"
date: 2006-10-28
forum: General Help
---

### Post by titaniumlou on 2006-10-28
Ok, so I recently upgraded my laptop to Edgy and now I'm having issues with the bootup screen which typically shows a progress bar and some nice graphical information about the system services as they are starting up.

Originally I wasn't getting any splash screen at all (after the grub menu selection) and on the main console (ctrl-alt-F1) I would see "usplash: setting mode 1920x... failed"

I've gotten something to come up by using the kernel boot parameter vga=755 (and 753 worked too) which I found at this thread:
[http://www.ubuntuforums.org/showthread.php?t=258484](http://www.ubuntuforums.org/showthread.php?t=258484)

My question is, how can I get all of the information to show up on the screen when the system is running through the bootup sequence?

I found another thread which mentioned re-making the usplash-theme-ubuntu.so file but I would prefer not to have to do that, though I realize I might be forced to.

In case it matters at all I'm using an IBM T43 with a Radeon X300 graphics card.

Thanks in advance!

---

