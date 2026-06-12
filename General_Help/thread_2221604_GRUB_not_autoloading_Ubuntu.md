---
title: "GRUB not autoloading Ubuntu"
date: 2014-05-02
forum: General Help
---

### Post by damian_ on 2014-05-02
Hey guys,

I've just installed a fresh 14.04 on a HP ML110 G5, everything seemed to go alright during the process, except for when it booted it came up saying /boot was unavailable, but it still booted. I've since fixed that and can read /boot.

The issue now is that Ubuntu doesn't autoload at the GRUB loader, it waits for user input to tell it which OS to boot (there's only one OS installed).

I've been through a number of posts on here which are saying to modify the grub.cfg, grub.d/00_header for the timeout, however this doesn't seem to do the trick, it's just like the timeout doesn't exist.

Any help would be appreciated, this guy will be headless soon and it will be a little annoying having to plug a keyboard in every time I reboot :P

Thanks,

---

