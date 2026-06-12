---
title: "Help! I accidenally erased GRUB and now I can't boot!"
date: 2008-05-18
forum: General Help
---

### Post by Commodore13 on 2008-05-18
I was really exited about the Wubi feature in 8.04 and I thought that it would be a good alternative to managing an entirely seperate partition. I had the idea to delete my Ubuntu partition and install Wubi inside of Vista Premium instead. I went to diskmgmnt.msc and deleted the partition, when I went to restart and install wubi, I realized that I had erased GRUB!! it came up with the err message 17. I'm currently typing this from my emergency DSL-N CD I have in my toolbox. Please help me!

---

### Post by ago on 2008-05-18
Even deleting wubi/wubildr you would still be able to boot into Vista. Wubi does not replace the windows bootloader. So you must have deleted  something else as well... And wubi does not use grub, but grub4dos.

---

### Post by meierfra. on 2008-05-18
> Even deleting wubi/wubildr you would still be able to boot into Vista

But the OP deleted a regularly installed Ubuntu partition (not a Wubi installed)

This thread tells you how to fix your MBR

[http://ubuntuforums.org/showthread.php?t=740221]("http://ubuntuforums.org/showthread.php?t=740221")

Or you can use Supergrub (see my signature)

---

### Post by ago on 2008-05-18
If ubuntu was installed without wubi, and you wiped out the main bootloader, then yes you will need to install a new bootloader from a CD. You can use linux (grub-install /dev/XXX) or a vista bootlader or anything else you fancy. Grub is normally a good choice. Of course you will also need to add an appropriate menu.lst.

---

