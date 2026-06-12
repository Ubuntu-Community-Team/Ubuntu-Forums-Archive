---
title: "archiving floppy disks - creating a floppy image"
date: 2007-12-08
forum: General Help
---

### Post by megamania on 2007-12-08
I need to archive quite a few floppy disk. I want to do this to be sure that if/when the floppies stop working, I'll be able to re-create them.
Most of them contain retro software which needs to be on a floppy to be used again, and I'd like to go with bit-by-bit copy to be sure everything will work.

I tried a simple
```
sudo dd if=/dev/sdb of=~/Desktop/floppy.img
```
and I came up with an image on my desktop. I am able to mount and open it, but I'm not sure it would work again if I put it back on a floppy.

I searched for a while and saw that some suggest using:
```
dd if=/dev/fd0 of=floppy.img count=1 bs=1440k
```
which means they think it's important to specify the size of the floppy disk.

Since I have to create images of *many* floppy disks (some are 720KB, others are 1.4MB), before I go ahead using the wrong method I'd like to have some directions.

Should I check the type of floppy I'm going to copy and specify its size each time? Are there other important things I should keep into account?

---

### Post by megamania on 2007-12-10
*bump*

can anybody help please?

---

