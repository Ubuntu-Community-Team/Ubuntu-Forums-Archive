---
title: "move to trash freezes nautlius for 15+ seconds"
date: 2007-01-12
forum: General Help
---

### Post by harty83 on 2007-01-12
I'm using edgy.   Whenever I delete something or send it to the trash, nautilus freezes for 15+ seconds.  This does not happen if I shift-delete; only if I move it to the trash.  Any clue as to what would be the cause of this?  

As you can imagine, this is quite annoying.

Thanks!
Alan

---

### Post by earobinson on 2007-01-12
do you have more than on hd, could it be copying the files across hd's?

---

### Post by harty83 on 2007-01-12
> **earobinson said:**
> do you have more than on hd, could it be copying the files across hd's?

Nope just one hard drive.

---

### Post by elj4176 on 2007-01-19
I am having the same problem and shift-delete works for me too.  I have one hard drive but several partitions (dual boot dell). This just started a few days ago and it is getting really really annoying.
I do have a couple of network drives that are in the fstab but they are working fine. I get hte same freeze of nautilus when I attach my iaudio mp3 player/usb drive. It used to work fine and now it takes a long time to automount and then the same time to browse the folders on it.

---

### Post by elj4176 on 2007-01-19
hmm - I took out all of my shared drives. Commented out the lines in the fstab. removed my usb drive and restarted X. Now my usb works right as does my trash. I left my fstab alone and just remapped my shares and all seems to be working right again. The only difference is now the network drives are not on my desktop.
Time to reboot and see if all still works right.

---

### Post by dimeotane on 2007-03-10
I have a similar problem.  Did you find it was related to having mounted SMB shared drives in fstab?

I'd comment them out to improve the freeze when doing a move to trash, but then I'd be back to mounting my windows SMB share using the command line.

---

### Post by harty83 on 2007-03-11
I ended up solving this problem by renaming my ~/.gconf folder which returned everything back to default.

---

