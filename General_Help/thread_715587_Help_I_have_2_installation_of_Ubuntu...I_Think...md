---
title: "Help I have 2 installation of Ubuntu...I Think.."
date: 2008-03-05
forum: General Help
---

### Post by Djanvk on 2008-03-05
Ok I just installed the 64bit installation of 7.10 and when I restarted GRUB showed under other operating system the othe 32 bit version, I thought the new one would just copy over the old one.

How Can I get rid of the 32 bit version?

Thanks


Also Windows XP is installed to.

---

### Post by Front187 on 2008-03-05
Did you actually try to boot into it?

If it gives Error 15: File not found, then that means it is just showing up because GRUB just kept the entry for it in there.  To fix this, simply edit /boot/grub/menu.lst

If it does boot into your old linux kernel, your best off formatting the drive and doing a clean install.  If it boots, make sure it is infact booting into your old linux kernel and not your new one before you format.

---

### Post by Djanvk on 2008-03-05
Yep it's booting into it.

---

### Post by Front187 on 2008-03-05
What are the contents of /boot/grub/menu.lst?

Just so we can make sure that both entries aren't pointing to the same file.

---

