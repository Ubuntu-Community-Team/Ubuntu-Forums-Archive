---
title: "Vista doesn't like ubuntu - need LOTS of help!"
date: 2008-04-21
forum: General Help
---

### Post by nappymonster on 2008-04-21
Hi all,
A while back i installed ubuntu and it was all fine. What i ultimately wanted was:
-Vista on my internal hard drive, untouched, working fine.
-ubuntu on my external drive, meaning i can set the bios to boot from external and use ubuntu, or set it to internal and boot into vista.

But, whereas for the most part it has been fine, i've come to realise that actually my computer is in an unusable state.

I'm going back to school tomorrow, and i'm going to need to be able to work on this pc. I do all school work on vista (i need office 07 and a few other apps. The office 07 ubuntu guide didn't work for me). Vista decides you've put the hd on a new pc if something major changes, and i think it saw ubuntu as this major change. But Since i've installed it, i've had alot of things not work:

-"This version of windows will expire in 30 days" (counting down, now saying 0 hours, even though i've entered in a new product key that MS gave us).
- Random restarts of vista
-I cannot install anything, since it says "Invalid Drive D:\" or words to that effect.

Now today i got GRUB error 17. So great. I can't boot into vista or ubuntu. I'm writing this from the gusty live cd.

Please tell me how to boot back into vista + ubuntu, (so getting rid of error 17) and make changes so that i can set the BIOS to external and boot into ubuntu for most uses, and setting it to internal for work.

Also, For a long while i thought /boot/grub was on the internal drive, because if i unplugged the external one it just gave the error 21, but it'son the external ubuntu drive, but if i unplug it GRUB still loaded? GRUB breaks so often i really want to be able to bypass it by changing the bios and completely going past it if need be.

And finally, i took a backup of the /boot/grub folder a couple of days ago: could restoring that help?

Thanks,
Nappymonster

UPDATE: After removing an external hd that was formatted as "Mac os X extended (Journaled)", it booted. Not sure why that caused a problem, as it has been plugged in for many boots. (Note this does not have leopard running on it yet, just failed installs :() Any suggestions regarding the other problems would be great.

---

### Post by Vermind on 2008-04-21
Hello,
if You add new hard drives, the numbers in GRUB may change. And so can the order of disks in Your BIOS. I don't boot from external hard drives with Vista, so I'm not sure what I can say about that.
If You installed grub with grub-install without giving it a hard drive to throw it to, or automatically, it probably put itself on Your primary hard disk, that is, the internal one. However, since Your Linux is on the external, the files that GRUB needs to mount any file systems and therefore boot any operating system, are on the external hard drive. So booting without the external drive will not work.
GRUB has two parts: the boot loader that resides on Your hard drive's master boot record, and files such as the GRUB configuration file and partition mounting stuff, that is on Your Linux boot partition. 

I recommend first installing Your GRUB on the external HD by booting Ubuntu, then running grub-install /dev/sdb, if sdb is Your external hard drive.

To fix the windows boot loader on the internal HD, I recommend running the windows fixmbr tool from the Vista disc or recovery partition.

---

