---
title: "Grub not booting XP after gparted change"
date: 2008-03-24
forum: General Help
---

### Post by Rippy on 2008-03-24
Okay, to start off, I should probably list off what I'd done so far:

- Installed Win2k, then installed Ubuntu. Grub handled this just fine.
- Installed XP. This overwrote Grub.
- Did a huge repartitioning of my drive. It went from this:

Win2k (20GB)
WinXP (20GB)
Ubuntu Hardy Heron (20GB)
Extended:
swap (2GB)
data (98GB)

to this:

WinXP (60GB)
Ubuntu Hardy Heron (20GB)
swap (2GB)
data (78GB)

- I fixed Grub with a LiveCD and these commands: sudo grub, find /boot/grub/stage1, root (hd0,2), setup (hd0), quit. (hd0,2 was what was returned by the find command)
- The menu still just had an entry for Win2k and none for XP, so I modified the name. I also had to change it from root (hd0,0) to rootnoverify (hd0,1) in menu.lst, otherwise I got Grub Error 13.
- Even with the right drive name, I now get "NTLDR is missing, Press CTRL + ALT + DEL to restart".

So, I think what messed things up was deleting the Win2k partition. I've done some googling and seen some suggestions of trying a FIXMBR off an XP boot CD, but right now I'm afraid of screwing things up further. It also seems like each partitioning problem is completely different, so I think it's best to get some input from you guys.

Oh, and some more info about my system:
OSes: XP and Ubuntu Hardy Heron (Yes, I read the sticky about Hardy Heron problems, but this problem really doesn't have anything to do with Hardy specifically, so I think it still belongs here)
Hard Drives: 1 160GB SATA drive, with 4 primary partitions (see above)

My menu.lst is included (as a .txt file)

Any help is greatly appreciated. Thanks!

Rippy

---

### Post by kbless7 on 2008-03-24
Well if your partitions are in the order that you listed them, it should go 

```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```

---

### Post by Rippy on 2008-03-24
Well yeah, that's what it SHOULD be. But trying that gives "Error 13: Invalid or unrecognized executable format". See, everything still has the same number that it had when Win2k was hd0,0.

0: Win2k
1: WinXP
2: Ubuntu
etc

to

1: WinXP
2: Ubuntu
etc

Know what I mean? I'm booting into Ubuntu using hd0,2 as well. The numbers haven't changed.

By the way, I'm not particularly familiar with drives and partitioning, so I apologize if I say anything wrong or ignorant. I don't know if a partion's number is supposed to "shuffle over" if a preceding partition gets deleted, but it certainly hasn't for me. And while this could be an issue of its own, I'm thinking it's something else that's preventing XP from booting. (since, for it to say NTLDR is missing, it must have already passed control over to XP, right?)

---

### Post by Rippy on 2008-03-25
bump? trying a fixmbr using an XP live cd didn't work, I had to restore grub again.

---

