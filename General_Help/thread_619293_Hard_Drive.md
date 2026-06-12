---
title: "Hard Drive"
date: 2007-11-21
forum: General Help
---

### Post by tezzaa on 2007-11-21
Is there a command that I can use to check the physical integrity of my hard drive?

Thanks

Terry

---

### Post by oneadvent on 2007-11-21
fsck i believe, but not on a mounted hd

---

### Post by tezzaa on 2007-11-21
Thanks for the reply.

I read this on Wikipedia:

"Fsck can also be run manually by the system administrator if there is believed to be a problem with the file system. However, running fsck on a **mounted file system** can potentially cause severe data corruption/loss."

What is a mounted hard drive/file system?

Tezzaa

---

### Post by skyjacker on 2007-11-21
> **tezzaa said:**
> Thanks for the reply.

I read this on Wikipedia:

"Fsck can also be run manually by the system administrator if there is believed to be a problem with the file system. However, running fsck on a **mounted file system** can potentially cause severe data corruption/loss."

What is a mounted hard drive/file system?

Tezzaa Maybe this will help.
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
From what I understand, you will have to do a Fsck command using the Install cd. this gets away from using the ubuntu Partitioned hard drive (which is "mounted").

---

### Post by oneadvent on 2007-11-21
> **tezzaa said:**
> Thanks for the reply.

I read this on Wikipedia:

"Fsck can also be run manually by the system administrator if there is believed to be a problem with the file system. However, running fsck on a **mounted file system** can potentially cause severe data corruption/loss."

What is a mounted hard drive/file system?

Tezzaa

the guy above me is correct, use the livecd.

a mounted drive is a drive that is now a part of your computer, another words it is able to be written to.

---

### Post by bingoUV on 2007-11-21
fsck will check the integrity of your file system, not your hard disk. Specific file system fscks (it is a plural) have the options for checking the hard disk for bad blocks, but they only work for their own file systems. badblocks is a program which works for any filesystem. It will tell you if there are bad blocks on your hard disk. It will take a long time. 
```

sudo badblocks /dev/sdX

```

If you want to learn about overall health of your hard disk, use smart. The first command is summary, second is for details
```

sudo smartctl -H /dev/sdX
sudo smartctl -a /dev/sdX

```

---

### Post by oneadvent on 2007-11-21
> **bingoUV said:**
> fsck will check the integrity of your file system, not your hard disk. Specific file system fscks (it is a plural) have the options for checking the hard disk for bad blocks, but they only work for their own file systems. badblocks is a program which works for any filesystem. It will tell you if there are bad blocks on your hard disk. It will take a long time. 
```

sudo badblocks /dev/sdX

```

If you want to learn about overall health of your hard disk, use smart. The first command is summary, second is for details
```

sudo smartctl -H /dev/sdX
sudo smartctl -a /dev/sdX

```

nice catch.

---

### Post by tezzaa on 2007-11-22
thanks guys for all your replies

Tezzaa

---

### Post by oneadvent on 2007-11-22
mark thread as solved

---

