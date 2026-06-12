---
title: "dual booting..."
date: 2007-06-22
forum: General Help
---

### Post by rob1101 on 2007-06-22
ok so i already have ubuntu installed and the main partition takes up all of the space. how do i edit that and install xp in a different partition. also what do i have to edit so they will boot properly and so i can select which os to boot.

---

### Post by Page on 2007-06-23
If you install XP, you are going to have to reinstall grub since winxp's installer will overwrite the MBR (making your linux install inaccessable) , so make sure you have a second way to boot into ubuntu before you try this. 

 you could try resizing your hd?1 partition. (? = drive letter). with something like gparted or qtparted to create a chunk of free space. I'm not sure how ext3 filesystems respond to being resized, but I know that NTFS reacts badly to it.  In any event, be ready for data loss in case something goes wrong.

You could also try putting in another hard drive as a slave and putting windows on that. I recommend this because there is a lot less risk since you aren't changing existing partitions. You will probably still have to reinstall grub, though.

---

### Post by rob1101 on 2007-06-23
> **Page said:**
> If you install XP, you are going to have to reinstall grub since winxp's installer will overwrite the MBR (making your linux install inaccessable) , so make sure you have a second way to boot into ubuntu before you try this. 

 you could try resizing your hd?1 partition. (? = drive letter). with something like gparted or qtparted to create a chunk of free space. I'm not sure how ext3 filesystems respond to being resized, but I know that NTFS reacts badly to it.  In any event, be ready for data loss in case something goes wrong.

You could also try putting in another hard drive as a slave and putting windows on that. I recommend this because there is a lot less risk since you aren't changing existing partitions. You will probably still have to reinstall grub, though.

well putting in a HDD is out of the question because it is a laptop :P i think im just gonna reformat install windows then install ubuntu. that SHOULD go smoothly without toomany problems right?

---

