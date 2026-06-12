---
title: "MAJOR problem with Gutsy Gibbon..."
date: 2008-05-19
forum: General Help
---

### Post by kailynleto on 2008-05-19
I installed Gibbon (first install because I wasn't satisfied with Heron) on my Seagate FreeAgent 250 GB external (though I wiped it clean), and the GRUB bootloader is letting me load neither Ubuntu nor Windows XP.  It still sees XP, it just won't load.

What do I do?  This is not technically my computer...

BTW, it's Error 22, and I don't have the XP boot disk.

---

### Post by kailynleto on 2008-05-19
Question.  Can I just delete the partition I use to boot Linux?

---

### Post by meierfra. on 2008-05-19
> Question. Can I just delete the partition I use to boot Linux?

That won't help.

Do you get Error 22 before the Grub Menu appears? 
If yes you need to reinstall Grub. If your bios are able boot  from the external drive, I recommend to install grub to the  external drive:

sudo grub
find /boot/grub/menu.lst
root (hd1,0)      #Use the output from the previous line
setup (hd1)       #  Use the first number from (hd?,?)

Click on FixGrub in my signature for a more detailed description. 

But you should NOT do this if the grub menu appears at boot. Just come back here.

---

