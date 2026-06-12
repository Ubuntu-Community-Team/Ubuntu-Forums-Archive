---
title: "Resizing partition"
date: 2007-06-01
forum: General Help
---

### Post by American_Outcast on 2007-06-01
I am having a problem with resizing my partition. At first I wanted to duel boot, but after seeing how well Ubuntu was and how much better CrossOver got, I decided to just delete XP on my main computer. This is the problem. When I first installed Ubuntu I had hda1 for XP, hda2 for swap and hda3 for Ubuntu. I deleted the XP partition. I was able to move the swap partition to the beginning. I tried to resize the Ubuntu partition and then kicked myself. I was trying to resize it while running Ubuntu, I know duh, lol. So I rebooted with the Ubuntu CD and then I tried to rsize the partition (as root.) That didn't work. So I have 40G just sitting there and I can't resize Ubuntu. Am I missing something? Please don't tell me I have to reinstall Ubuntu, lol, I just got it set up the way I want it. Anyone have an ideas?

(Also I am buying a copy of CrossOver today and I don't really want to buy any commercial programs for partitioning.)

Thanks in advance

---

### Post by merlinus on 2007-06-01
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it as an .iso (disk image), and boot from it.

Good luck!

-merlin

---

### Post by jamesjtucker on 2007-06-01
The other option would be just to create a new partition using that space, and choose a mount point that you would want to access it from, say /opt/music or /home/myusername/data/  Its an easier solution.

---

### Post by American_Outcast on 2007-06-01
merlinus & jamesjtucker, thanks for the ideas and help.

I tried that Gparted liveCD. It didn't work. It won't let me move or resize hda3. It is at the end of the partition bar, maybe that is the problem? It was unmounted with the Ubuntu CD and Gparted CD.

On hda3 I have about 11G left out of 40 (approx.) I also have a second 80G HD split into two partitions for storage, etc. I may try using the other 40G on HDA for just Crossover and VM's.

---

### Post by confused57 on 2007-06-01
Maybe you can use the gparted live cd to do a filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by American_Outcast on 2007-06-01
I just did that with the Ubuntu CD. Everything looks normal and no bad blocks. GParted just doesn't like me, lol.

---

### Post by American_Outcast on 2007-06-01
I think I am getting closer to the problem. I used the terminal, ran cfdisk and deleted that partition and created a linux one on hda1. Then I ran, using sudo, 


sudo mkfs ext3 /dev/hda1


And this is the error I got,

mke2fs 1.40-WIP (14-Nov-2006)
mkfs.ext2: invalid blocks count - /dev/hda1


Did I do something wrong? That partition worked fine before with XP and the hard drive appears to be fine as well, that is where I am running Ubuntu (hda3). I am guessing, errr.... I know I am missing something here :(

---

### Post by American_Outcast on 2007-06-01
I finally did it. I am still not sure what the problem was, but I found the solution. Gparted deleted XP NTFS without any apparent problems. It also created a logical volume but no matter what I did I could not write to it, etc., or if I deleted it I could not resize Ubuntu hda3. I rebooted so many times I was starting to have XP flashbacks.

So I tried a few things with the Ubuntu CD, Gparted CD and finally the SystemRescueCD. I used cfdisk and fdsik, nothing worked and I kept getting sector errors, etc. When I was using cfdisk I was trying to create a primary partition, but everytime I did it would not write the mkfs ext3 to it afterwards. So I was just about ready to give up when I remembered the gparted was creating a logical partition. So I did that through cfdisk. Then I rebooted with the Gparted disk and tried writing an ext3 to that partition.... and it WORKED, lol. So I deleted that partition and resized hda3.

I have no idea what the problem was or if I did it the long way, but I don't care, lol, the partition problem is over.

---

