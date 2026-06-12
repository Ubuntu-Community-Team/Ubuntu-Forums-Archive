---
title: "Removing xp partion and resizing hda3 primary ext3"
date: 2006-11-06
forum: General Help
---

### Post by johnny9794 on 2006-11-06
Ok guys I have decided that I will no longer need my windows xp operating system.

I do have grub installed.
I am running dual boot system.

I have hda1 as xp partition, hda2 as 5 gig partition swap, hda3 as primary ext3.

I would like to remove my hda1 xp partition and resize my hda3 partition to take up the rest of the size that xp has after I remove hda1 "xp partition". 

Now would my system screw up or would files become corrupted if I resize my hda3 primary ext3 partion to be larger?

Do i need to remove grub? I would like to keep grub for the fact of locking it which is a great option.

I know how to resize, make partions, ect and use gparted.

I do have my documents backed up just in case of a failure.
Thanx.

---

### Post by Najand on 2006-11-07
Wow, 5G of Swap is too big. Well, How can you add your first partition to the third one? Hmm, Do you really need to add it to your third partion? If not, why not just formatting it as EXT2 or EXT3 and use it to back up data and keeping you music/data files. 
For changing grup, sudo to edit /boot/grub/menu.lst and comment the Windows XP part at the bottom of the file with # signs at the begining of lines and save it.

---

### Post by johnny9794 on 2006-11-07
> **Najand said:**
> Wow, 5G of Swap is too big. Well, How can you add your first partition to the third one? Hmm, Do you really need to add it to your third partion? If not, why not just formatting it as EXT2 or EXT3 and use it to back up data and keeping you music/data files. 
For changing grup, sudo to edit /boot/grub/menu.lst and comment the Windows XP part at the bottom of the file with # signs at the begining of lines and save it.

Well ok i am new at linux anyhow but if 5 gig swap is to big what should i have it at? 2 gig swap?

and as for partition 1. Why don't I use it for backing up data n such is because i have a second hdd for that :).

---

### Post by Najand on 2006-11-07
Hmm, well... It depends, but usually twice the size of your RAM sounds fine.

---

### Post by Atomic Dog on 2006-11-07
A gig would be fine.  Two is OK too I suppose.  5 is way excessive!  I match the amount of ram I have.  I have a gig or ram so I have a 1 gig swap.

---

