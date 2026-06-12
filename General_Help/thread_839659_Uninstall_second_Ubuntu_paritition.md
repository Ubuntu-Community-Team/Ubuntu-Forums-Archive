---
title: "Uninstall second Ubuntu paritition?"
date: 2008-06-24
forum: General Help
---

### Post by ybd on 2008-06-24
I made the switch to Ubuntu (Hardy) about two weeks ago. It rocks!
However a few days ago, due to my lack of knowledge in Linux I did something dumb that required a reinstall (chown'd my root drive) but I reinstalled into a new partition, so while the new installation works fine I still have the other partition that was used up by the older Ubuntu installation... how do I uninstall it, and delete that partition?

All the guides to uninstall that I saw where for people who dual booted XP and Ubuntu and wanted to keep just XP.

---

### Post by kk0sse54 on 2008-06-24
Is Ubuntu the only OS on your computer because then just boot up the liveCD go into Gparted and delete the old partition and just expand the new partition to take up your whole HD except for of course the swap.

---

### Post by forestpixie on 2008-06-24
It might mean that you have to resize an extended partition depending on how you installed it - both times  :)

Be aware also that resizing might change the UUIDs and could cause problems with you fstab and partition mounting.

---

### Post by ybd on 2008-06-24
> **C!oud said:**
> Is Ubuntu the only OS on your computer because then just boot up the liveCD go into Gparted and delete the old partition and just expand the new partition to take up your whole HD except for of course the swap.

I also have XP installed, forgot to mention it - sorry.
I'm guessing I can uninstall it through XP? But I want to keep GRUB (obviously) so I can still dual boot the newer Ubuntu and XP.

---

### Post by kk0sse54 on 2008-06-24
You can still use Gparted to delete the old partition and expand on the new one while leaving your XP partition untouched. Just keep in mind what forestpixie said.

---

