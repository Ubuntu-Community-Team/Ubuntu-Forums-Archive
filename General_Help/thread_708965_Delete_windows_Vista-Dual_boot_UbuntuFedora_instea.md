---
title: "Delete windows Vista-Dual boot Ubuntu\Fedora instead"
date: 2008-02-26
forum: General Help
---

### Post by faineant7698 on 2008-02-26
Hi I want To remove windows vista Home basic as I am currently dual booting with it.  Instead I want to have my Ubuntu linux and Fedora linux dual booted instead.  I just want to find the best way of going about this so I don't end up damaging my Ubuntu partition.  

Thanx in advance for any help you may have on this matter.:guitar:

---

### Post by em3raldxiii on 2008-02-27
You can probably just safely delete the partition that has VISTA on it, and then you can create and reformat it to whatever you would like.  You may also be able to just add the partition to your existing Linux partitions, but I think you are likely better off just formatting it to EXT3 and having it as an "extra drive" (unless you need the space for something specific).

Worst case scenario, you might gibble your GRUB (the boot loader) but that is pretty easy to fix either with your Ubuntu installation CD or even from within Ubuntu.  I don't forsee any negative repercussions from deleting your Vista partition.

---

### Post by faineant7698 on 2008-02-27
Ok the deletion of windows went great and the install of fedora was great, but I did screw up GRUB so will try and fix this using the ubuntu live install.

---

### Post by faineant7698 on 2008-02-27
Screwed Grub re-installed grub using ubuntu live cd but fedora not showing up in grub menu.  either i just have fedora or i just have ubuntu in grub. need both please help!!!:lolflag:

---

### Post by em3raldxiii on 2008-02-29
Strange ... LOL.  Well, if you know where the various OSs are installed, you should be able to manually add specific lines to your GRUB menu for each operating system, then you should be able to boot either.

So I guess we need to know your partition arrangement and we can get you figured out.

---

