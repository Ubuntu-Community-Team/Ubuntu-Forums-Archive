---
title: "Fixing GRUB"
date: 2008-05-13
forum: General Help
---

### Post by Nomsain on 2008-05-13
I installed Windows XP a while back and it overwrote GRUB. (I did this because I hated Vista..)

Now I have GRUB reinstalled but whenever I select Ubuntu 7.10 from the list it says something like 'This cannot be mounted' 

I don't remember the exact message.. (but I'm hoping someone will help me)

I will restart my computer now to get the exact message.. (It would've helped if I knew it before hand)

---

### Post by Caram on 2008-05-13
You have a partition for Ubuntu set up? Did you just reinstall GRUB or Ubuntu as well? Installing XP might have wiped your Ubuntu partition. Try booting from a LiveCD and see if you can find your filesystem.

---

### Post by Nomsain on 2008-05-13
Ill try to see if my partition was wiped.. I hope not :(

---

### Post by Nomsain on 2008-05-13
> **Nomsain said:**
> Ill try to see if my partition was wiped.. I hope not :(
I just checked and it was not wiped out.

---

### Post by Caram on 2008-05-13
Alright, what you'll want to do is run a LiveCD. Mount your filesystem, go into /boot/GRUB/menu.lst Open that up. Now, if you are running Hardy, You'll need to identify what order the partitions are in. I.E. if you look on a partition editor/disk analyzer it will show them in a line. See if you have something like

> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,**3**)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a19e0584-67b5-4afb-a0df-f296af799d8d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

I'm guessing the bold is what you have wrong. For example, I have an NTFS, a FAT32, and then my EXT3 in that order, so my number is three. If your Ext3 partition is the first one, your number needs to be one. I'm sorry if this is rather hard to understand.

---

### Post by Nomsain on 2008-05-13
Thank you so much for trying to help me but I have three questions.

Will this be different because I'm running 7.10?
How do I mount my filesystem?
How do I find out the number of my linux partition?

---

### Post by Caram on 2008-05-13
Okay, I've done a picture. [http://img247.imageshack.us/my.php?image=screenshotxa1.jpg](http://img247.imageshack.us/my.php?image=screenshotxa1.jpg) shows my partition editor. I'm pretty sure the LiveCD has a partitioner in it that will show you something similar to this. 

On how to mount your filesystem, on the LiveCD go to places, Computer, and mount the your Ext3 Filesystem.

And yes, yours will most likely be different from mine, but there will probably be something similar.

---

### Post by unutbu on 2008-05-13
Careful -- GRUB numbering starts at 0, not 1.
Take a look at [http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention).

To find the right number, boot from the LiveCD, open a terminal and run
```

sudo grub
```

At the grub prompt type

```
root ( <TAB><TAB>
```

Yes, that's an open parenthesis followed by 2 tabs.
GRUB will try to complete the command for you. The first tab should return hd0, unless you have more than one hard drive, in which case you might have to  type the 0 yourself. The second tab will give you a list of partitions, numbered as GRUB sees them, followed by the filesystem type. You can usually guess which partition corresponds to the Linux root filesystem because it's and ext2 or ext3 filesystem (usually) and comes before any other ex2/ext3 filesystem (usually). 

Erase that line at the grub prompt, and say exit.

Now type
```

gksudo gedit <where-you-mounted-your-harddisk>/boot/grub/menu.lst
```

and edit the boot stanza per Caram's suggestion, but with the number you found above.

---

### Post by Caram on 2008-05-13
Heh, I knew there was something wrong >_<

His method is more orthodox as well :P

---

### Post by Nomsain on 2008-05-13
Thanks to both of you very very very much.

---

