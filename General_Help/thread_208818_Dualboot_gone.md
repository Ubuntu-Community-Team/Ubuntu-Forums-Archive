---
title: "Dualboot gone"
date: 2006-07-04
forum: General Help
---

### Post by bekok on 2006-07-04
Hey,

Today I wanted to delete Windows from my pc, to give it a fresh reinstall.
I encounterd some serious problems though and I hope anyone can help me, else i'm kinda screwed :).

I used a windows cd to delete disks "C:\ (windows stuff) & D:\ (game and stuff like that)", which all went fine, and I just insalled windows on those disks. Windows did his thing and set up everything good, but when I rebooted, the Dualboot screen didn't show up and it automatically booted Windows.

That's the strange thing, my whole dualboot is gone and I'm only able to boot into Windows. In the meanwhile i've delete windows again to see if it would boot into Linux, but it says i have to put in a disk with an installation program.

I hope anyone can help me, caus i'm kinda stuck here :(

---

### Post by Ramses de Norre on 2006-07-04
You need to reinstall grub
```
grub
root (hd0,0) #disk and partition containing /boot/
setup (hd0) #disk containing mbr (the one you boot from)
setup (hd0,0) #should be same device as first command
quit
sudo update-grub
```
And grub should be installed

---

### Post by bekok on 2006-07-04
Do I have to do that onto the live cd of Ubuntu? (caus i can't get into linux)

---

### Post by Ramses de Norre on 2006-07-04
Yes indeed.

---

### Post by bekok on 2006-07-04
O, i forgot to mention, Linux is installed on a different HD then Windows. Should that make a differennce? 

And i don't fully understand these;
disk and partition containing /boot/ {Should that be the windows or linux one?}
disk containing mbr (the one you boot from) {same is above}

---

### Post by Ramses de Norre on 2006-07-04
The device and partition containing boot is probably your / partition (except when you made a seperate /boot partition), grub counts everything from zero, so hdc1 becomes hd2,0.

The disk containing the mbr is the disk your bios boots from, so probably the hard disk you've got windows installed on.

---

### Post by flarkit on 2006-07-04
Windows is very kind and overwrites whatever's written in the MBR. As stated, you should boot into the LiveCD, run ther terminal and execute the commands described.

Your XP and Ubuntu installations should still be quite usable after that though.

On the point of "/" and "/boot"... these are basically Linux terms, which do not refer to the XP installation (unless you explicitly mount things differently). So those directories should reside on your Linux disk and in no way refer to Windows.

---

### Post by bekok on 2006-07-04
It worked, I've got Grub back :D.
Danx for the help guys

---

