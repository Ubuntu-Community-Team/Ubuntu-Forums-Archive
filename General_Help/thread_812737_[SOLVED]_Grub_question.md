---
title: "[SOLVED] Grub question"
date: 2008-05-30
forum: General Help
---

### Post by thelugnut on 2008-05-30
Is it possible to have three operating system choices on the grub menu?

I now have Ubuntu 8.04 and Windows XP and everything is working fine.

I have a partition available on my hard drive, ( I only have one hard drive) and would like to use it to look at other Linux Distros.

I don't want to replace Ubuntu, I just want the choice to select another one when I feel like investigating.

Can this be done?

Thanks

---

### Post by danwood76 on 2008-05-30
Easily, especially if its another distro.
When installing the other distro just tell it to install grub to the partition, then you can chainload the partition as you do with windows.
Obviously this leaves you with 2 grubs.

Another way to do it is to not install grub at all from the new distro and just add its kernel and boot options to the grub file and /boot folder.

---

### Post by thelugnut on 2008-05-30
danwood76 - Thanks for the reply.

Could you elaborate on the second possibility?

> Another way to do it is to not install grub at all from the new distro and just add its kernel and boot options to the grub file and /boot folder.

I pretty new at this, so I need some details, if you have the time.

---

### Post by danwood76 on 2008-05-30
What I would do is tell the distro installer to install grub to the partition (not entire disk)
That will generate a menu.lst with the correct kernel arguments etc. to save you having to do it.

I would then copy the grub entry for your new OS into your current menu.lst and update the hard drive pointers if necessary. (root (hdx,x))

I havent actually tried this, I have done a similar thing before with a seperate /boot partition before.
It should work fine though as long as you get the partition numbers correct.

---

### Post by thelugnut on 2008-05-30
All right danwood76, I'm on it. Or I will be on it. Got to shoot off for the rest of the day now. Things to do, people to see ...

Much obliged for your answers. I'll post back when  get a chance to incorporate your suggestions, which should be this evening or tomorrow morning.

---

### Post by thelugnut on 2008-05-30
And so my problem has been resolved, thanks to danwood76.

Everything is up and running.

Much obliged to you.

:guitar:

---

