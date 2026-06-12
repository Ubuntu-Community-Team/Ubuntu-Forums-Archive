---
title: "Need GRUB Help !!!"
date: 2006-12-03
forum: General Help
---

### Post by deanhopkins on 2006-12-03
Wow, argh!

I was fiddling with the menu.lst earlier, customizing it. I done something wrong, it was ok, I had backed up menu.lst. I brought in the backup, then done something wrong again. Oh noes, no backup.

So I installed GRUB from a howto on here (setup (hd0) )

Now I have GRUB on my MBR, and have no way to get rid of it!

When I boot my PC, all I get is:

grub >

How can I remove GRUB from my mbr?! At least so I can put the windows MBR back on, or re-install GRUB correctly.


THANKS for helping ASAP!!!

---

### Post by pay on 2006-12-03
I don't think that you need to reinstall grub, you just need to configure it. But to answer you question, to reinstall the windows bootloader, put in the windows cd and boot into the recovery console and type```
fixboot
fixmbr
```

---

### Post by deanhopkins on 2006-12-03
Ive already tried that, and fyi, the command is fixmbr :)

It STILL persists to booting grub, which is why im realling confused, as the windows recovery console didnt report any errors whatsoever.

---

