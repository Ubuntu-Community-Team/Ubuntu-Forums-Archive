---
title: "Boot has no/very little progress detail? (edgy server, no splash)"
date: 2007-03-15
forum: General Help
---

### Post by dudinatrix on 2007-03-15
I just finished an Edgy server installation (using the amd-64 bit iso) complete with LVM, hardware RAID 1, yadda yadda yadda. Anyway, the boot progress has me curious... It starts normally, loads the kernel, and then just displays my 4 LVM logical volumes, and the results of the disk checks. Then it finishes at the login prompt.

Shouldn't there be more detail? What happened to the other stuff like.. Starting Apache [ ok ], starting MySQL [ ok ], Configuring network devices [ ok ], and all that? Why is it just showing very minimal disk related progress, is this something just for Edgy servers?

There's no splash screen or anything, so its not an issue of the stuff being "hidden", or a progress bar or anything. It's still a text boot, there's just not much detail!

The system itself seems fine.. Apache/etc is running, there are no errors (except for one LVM checksum issue, but I think thats ok).. it seems fine, it just looks a little naked at boot!

Ideas?

---

### Post by bernied on 2007-03-15
Have a look in /boot/grub/menu.lst
On the kernel line of your preferred boot option  there may be a quiet option, you can remove this without fear. There may also be a quiet option on its own line. Same deal.

Sometimes those rows and rows of meaningless text can be comforting.

---

### Post by dudinatrix on 2007-03-15
> **bernied said:**
> Have a look in /boot/grub/menu.lst
On the kernel line of your preferred boot option  there may be a quiet option, you can remove this without fear. There may also be a quiet option on its own line. Same deal.

Sometimes those rows and rows of meaningless text can be comforting.Indeed!

I did remove the quiet option that was on its own line, which didn't do the trick... but I didn't check to see if there was another quiet option thrown in there somewhere. I'll take another look tomorrow when I'm back at work, thanks!

---

