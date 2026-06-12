---
title: "Horror: Win2k made my pc unbootable!"
date: 2007-07-30
forum: General Help
---

### Post by hoboken on 2007-07-30
OK, I know this doesn't deal with ubuntu directly, but incidentally my ubuntu partition is unbootable now... so here goes.

In order to play an older game (black & white, damn it to hell) I installed windows 2000 on my system. The install worked, the game didn't, and now all that is bootable is windows 2000. It seems to be in win2k booting mode, because there is some sort of bootloader with win2k and winxp, but when I select xp it expects another win2k install and spits out an error.

I tried using the ubuntu direct install cd, but it doesn't recognize the partitions on my disk. It just comes up with my hard disk as one block. The partitions are definitely there, because I can explore them in win2k, through a program I had on my XP install.

So, what's the dillyo? Will I be able to get my partitions back? Any solution from all you fabulous people?

Thanks!

---

### Post by logos34 on 2007-07-30
> I tried using the ubuntu direct install cd, but it doesn't recognize the partitions on my disk. It just comes up with my hard disk as one block. 

I assume you mean the ubuntu live cd.  one block, hmm...What does

**sudo fdisk -l** (the letter L)

show?

---

### Post by hoboken on 2007-07-30
Nah, I meant the exact opposite :) The livecd ran super slow for me so I installed ubuntu using the alternate installer, the non graphical kind. I'm not sure where I could input your command.

The partition thing I'm talking about, where it usually showed all my partitions, has turned into 

Blank (an empty slot, literally blank, not a blank partition)
My harddisk
Blank

Any ideas?

---

### Post by logos34 on 2007-07-30
Try SuperGrub CD.
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

### Post by hoboken on 2007-07-30
Thanks. Looks like it should work.

---

