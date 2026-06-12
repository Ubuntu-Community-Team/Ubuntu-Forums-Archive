---
title: "Best Disk Imaging Applications"
date: 2008-01-27
forum: General Help
---

### Post by DeaconJones on 2008-01-27
Hi all,

Need to image some brand new drives. In your opinion, what are the best Linux HD imaging apps available.

Thanks

DJ

---

### Post by heindsight on 2008-01-27
I'm assuming you want a snapshot of the filesystem? I'd use dd
for example
```
dd if=/dev/sdb of=sdb.img
```

and to restore the image to the disk:
```
dd if=sdb.img of=/dev/sdb
```

EDIT:
be careful with dd, read the man pages and make sure you know what you're doing. it is possible to destroy a filesystem if you get the command wrong...

---

### Post by DeaconJones on 2008-01-27
Yes. Well, the OS and all installed apps. Basically all data on the partition, excluding empty space. I'd like to copy to an external HD, assuming the external HD is detected. Is there an option with dd to limit the size of the output file. So, say I have a 80 GB drive, with only the first 15 GBs written to, what would the command be to limit the output file to the first 15 GBs?

Edit: Reading man pages now

---

### Post by heindsight on 2008-01-27
dd is a very low-level way of doing things. It just copies data from an input file to an output file. It doesn't understand file systems. You could use the count argument to specify how much data to copy, but using that to make an image of part of a filesystem will result in a broken copy of the filesystem. 

If you need something that ignores unused space in the filesystem, you're going to have to find some more sophisticated higher level tools. I'm afraid I couldn't help you with that though -- haven't ever needed it...

---

### Post by heindsight on 2008-01-27
Just had a thought, I'm not sure it will work as I've never tried it, but maybe you could use dd to make an exact copy of your filesystem (ie an 80GB copy of your 80GB fs) and then use resize2fs (assuming it's an ext2 or ext3 filesystem) to shrink it.

---

### Post by wolfen69 on 2008-01-27
ghost4linux? [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by PinkFloyd102489 on 2008-01-27
You can use dd to use up the first 15GB of the drive. All you need to do is make a partition at the front of the drive the same size as the image you're copying. Then either make another partition for your other stuff or expand the partition that you copied out.


Also, you can go directly from one drive to the other with dd, if you want to make it a one step process instead of a two step process if you have both drives attached.

```

dd if=/dev/sourcedrive of=/dev/destdrive

```

---

### Post by heindsight on 2008-01-27
> **PinkFloyd102489 said:**
> You can use dd to use up the first 15GB of the drive. All you need to do is make a partition at the front of the drive the same size as the image you're copying. 

perhaps I misunderstand what you mean, but if you use dd to copy just the first 15GB of an 80GB filesystem, the resulting copy will not contain a usable filesystem.

---

### Post by PinkFloyd102489 on 2008-01-27
It will. Just create a blank partition the size of the RAW image and then use dd to copy it over.

---

