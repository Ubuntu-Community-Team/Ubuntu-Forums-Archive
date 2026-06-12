---
title: "Ubuntu, WIN XP and dual boot"
date: 2008-06-02
forum: General Help
---

### Post by PowerPig on 2008-06-02
Hi!:(:(:(:(:(

Total newbie nad I have a (realy) bad feeling about this question.
My brother took my laptop and installed Ubuntu on it. Ok. I turned on laptop and when it starts there is only Ubuntu. (1st - GOD!!!)
I pressed 'Esc' in GRUB loader and there is onyl 3 Ubuntu things. (2nd - OH GOD!!!) My question.

ARE MY DATA (VECTOR FILES, DRAWINGS,...) LOST FOR EVER???:(:(:( CAN I GET THEM SOMEHOW WITHIN UBUNTU?

I have no boot dual or anything else!

TNX 4 your help!

---

### Post by lisati on 2008-06-02
It is possible that your brother accidentally clobbered Windows. 
P
More technically-competent people than myself will be able to guide you through discovering if Windows is still there on your system. Don't be surprised if they ask you to go to the terminal (it's on the "Applications"->"Accessories" menu) and post the output of:
```
sudo fdisk -l
```

---

### Post by davidyu on 2008-06-02
Question&#65306; Did your brother created two partitions ? One for windows,the other for ubuntu ? 

1.If the answer is "no", it means only one Ubuntu partition. Nothing can do.
2.If the answer is "yes", then you can modify menu.lst under folder /boot/grub.

Add the following lines to menu.lst

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by luvr on 2008-06-02
Via the *"Places"* menu, open any folder (e.g., your home folder, Documents, or whatever). On the left-hand side of the window, you should see a list of the disk volumes that are present on your harddisk. See if you find anything that looks like it may be your Windows partition. Double-click it to *mount* it (i.e., make it accessible), and double-click again to open it.

---

### Post by Victormd on 2008-06-02
Open a terminal window, run the following command and post the output...
```
sudo fdisk -l
```
It should look something like this
[/quote]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4400    14860125   83  Linux
/dev/sda3            4401        4462      498015   82  Linux swap / Solaris
/dev/sda4            4463        9725    42275016    7  HPFS/NTFS[/quote]

If you don't see any "System" with HPFS/NTFS, then chances are your brother wiped out your HD... There are programs out there that allow you to recover formated HDs, but I don't know how they work with ext3/ntfs converted partitions.
Question... is your brother bigger than you?:lolflag:

---

