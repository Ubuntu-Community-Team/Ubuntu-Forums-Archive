---
title: "Urgent: Root filesystem gone due to mkswap!!"
date: 2007-02-21
forum: General Help
---

### Post by kolesarm on 2007-02-21
I was resizing my partitions, and I accidentally flagged my root filesystem (/dev/hda3) as swap, with mkswap - instead of /dev/hda4. Now everything is gone.

I've booted using the live cd, but I don't seem to be able to fix anything - anyone can help, please?

---

### Post by chggr on 2007-02-21
> **kolesarm said:**
> I was resizing my partitions, and I accidentally flagged my root filesystem (/dev/hda3) as swap, with mkswap - instead of /dev/hda4. Now everything is gone.

I've booted using the live cd, but I don't seem to be able to fix anything - anyone can help, please?

Did you only change the flag or did you erase the partition?

If you only changed the flag, things are pretty easy. Boot up using that live cd and follow these instructions:

1) Open a Terminal
2) sudo fdisk /dev/hda
3) press "t" to change the partition's id
4) press "3" to determine that it is the third partition
5) the id for linux is 83
6) press "w" to save the changes.

Things should work just fine.

PS. You should be very cautious when using fdisk, because you can easily ruin other partitions.

---

### Post by K.Mandla on 2007-02-21
> **kolesarm said:**
> I was resizing my partitions, and I accidentally flagged my root filesystem (/dev/hda3) as swap, with mkswap - instead of /dev/hda4. Now everything is gone.

I've booted using the live cd, but I don't seem to be able to fix anything - anyone can help, please?
Did you actually run a *mkswap /dev/hda3 *command? If you did, it might be gone forever. :shock:

---

### Post by kolesarm on 2007-02-21
> **K.Mandla said:**
> Did you actually run a *mkswap /dev/hda3 *command? If you did, it might be gone forever. :shock:

i am afraid i did actually run the mkswap command - and by mistake i typed in /dev/hda3 instead of /dev/hda4...

if have found a thread [here]("http://www.ubuntuforums.org/showthread.php?t=336290&highlight=undo+mkswap"), will try and use testdisk to at least recover my /home directory - funnily enough, i was repartitioning just so that i use a separate partition for /home so that nothing serious happends when i do something stupid like this in the future:(

---

### Post by kolesarm on 2007-02-21
yeah, and changing the flag back didn't help either. will most likely need to reinstall and hope i can save at least some files - all my multimedia are on a separate partition, however, it's all my univeristy projects that i might lose - and in that case i'm pretty much screwed

---

### Post by chggr on 2007-02-22
> **kolesarm said:**
> yeah, and changing the flag back didn't help either. will most likely need to reinstall and hope i can save at least some files - all my multimedia are on a separate partition, however, it's all my univeristy projects that i might lose - and in that case i'm pretty much screwed

Well, good luck! :(

---

### Post by kolesarm on 2007-02-23
TestDisk did not help either. I managed to reinstall ubuntu (on a different partition) and run PhotoRec, which did recover about 4Gb of text files - will have s look at them over the weekend.

---

### Post by kolesarm on 2007-02-24
ok, i'm all happy now - e2fsck saved my life, i now have **all** data back

---

