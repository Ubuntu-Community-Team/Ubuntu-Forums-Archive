---
title: "fixboot without delete grub."
date: 2008-06-02
forum: General Help
---

### Post by Netich on 2008-06-02
Hi. This is my problem: i had one disk with XP and ubuntu, and another one(the second one) with vista. I deleted Xp partition and resized so Ubuntu gets all the first disk.

But the boot for vista was in the XP partition, so i cant load vista now. I think i have to do 'bootrec.exe/fixboot', right?
So, is there any way to do it but not delete the grub? Only fix the vista partition, and redirect the grub chainloader to vista partition.

Thanks

---

### Post by yogo on 2008-06-02
You can mount your hard drive Vista/XP and edit the boot.ini.

Then just make sure to append what is appropriate to menu.lst IE

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by Netich on 2008-06-02
Thanks but in my vista partition there is no boot.ini. I think that's because it was Xp partition which had the loader. In fact my grub had a hd(0,0) entry for windows which was the xp partition. Now my grub point to the vista partition hd(1,0), but it cant load vista.

---

### Post by meierfra. on 2008-06-03
I doubt that "fixboot" and "fixmbr" will solve your problem. (Those two will fix the mbr and the boot sector, but  you are missing various boot files).  Check out  this link:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

I'm pretty sure that you won;t be able to boot into Ubuntu by the time you fixed your Vista problem.
But it is not all that difficult to Reinstall Grub (click on FixGrub in my signature)
Or you can use EasyBCD (see my signature)

---

