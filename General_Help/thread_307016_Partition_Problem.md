---
title: "Partition Problem"
date: 2006-11-25
forum: General Help
---

### Post by Pulshion on 2006-11-25
Hi

Im trying to install ubuntu on my friends HP. When i do manual partitioning after allocating size and formating the drive. It says that the format is unknown and the next part of installation doesnt recognize the partitions.

Using live 6.06 cd. Sata drive. 
Thanx

---

### Post by taurus on 2006-11-25
What filesystem did you pick?

---

### Post by Pulshion on 2006-11-25
I did

100gig ext3
1gig swap
100gig ntfs
the rest like 30 gig fat32

and all of them ended up unknown after formating

---

### Post by taurus on 2006-11-26
Is Ubuntu only OS on that machine?  I don't think the installer can handle formatting NTFS or FAT32.  To do that, you need to use gparted from the LiveCD first...

---

### Post by Pulshion on 2006-11-26
Right now it is. He wants to dual boot with windows. Mine formated fat32. Also my hd is IDE not SATA. Even if the install couldnt handle formating fat32 and ntfs, it would format ext3. It said unknown to all of them.

---

### Post by taurus on 2006-11-26
If he plans to install Windows on that machine as well, I recommend you make the first partition ntfs for Windows.  Then, use the second partition (fat32) to share data between Windows and Ubuntu.  Set the third partition (ext3) to /, and the last one to swap.  You can remove everything and start the partition table over with gparted from the LiveCD...

Again, use the gparted to format the first one to ntfs and the second one to fat32.

---

### Post by Pulshion on 2006-11-26
OK thank you very much. Ill try it tomorrow or something because im at home right now not at his house.

Also why in that order?

On my computer i have
NTFS
FAT32
SWAP
EXT3

is it bad?

---

### Post by taurus on 2006-11-26
Put Windows on the first partition just to make it happy and less headaches later...  You can also do something like

/dev/hda1 = ntfs
/dev/hda2 = ext3
/dev/hda3 = swap
/dev/hda4 = fat32

---

### Post by Pulshion on 2006-11-26
Is it bad what i have on my machine?

---

### Post by taurus on 2006-11-26
No, not at all.

---

