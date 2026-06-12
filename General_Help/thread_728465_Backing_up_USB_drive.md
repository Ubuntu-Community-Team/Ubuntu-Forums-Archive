---
title: "Backing up USB drive?"
date: 2008-03-18
forum: General Help
---

### Post by solarwind on 2008-03-18
Hey all, lets say I have a 1 GB USB flash drive with a bootable Linux distro on it. And let's say that I needed to reformat it. Before I do that, I would like to make a "disk image" of the flash drive so I can recover it after I do my experiments.

How would I be able to make this "disk image"? It is bootable so I want to be able to back up the boot sectors and all. Can this be done with *dd*? Are there other ways of doing it?

---

### Post by kidders on 2008-03-19
Hi there,

dd should do the trick. It makes a byte-for-byte copy of whatever you ask it to, so everything gets preserved.

---

### Post by solarwind on 2008-03-19
> **kidders said:**
> Hi there,

dd should do the trick. It makes a byte-for-byte copy of whatever you ask it to, so everything gets preserved.

So a simple *dd if of* will do?

---

### Post by kidders on 2008-03-19
Yep, it ought to. I suppose you could maybe gzip the result, so the blank space in the dump doesn't take up so much room. Anyhow, when you want to restore your disk to its original condition, you can just dump the data back onto it.

Two warnings, just in case you're not already aware of them...

1 - Make sure your USB disk is not in use while **dd** is running. Particularly when dumping your image back onto the device again, be sure no part of it is mounted, and try not to give your Linux any reason to probe its partition table, and so on.

2 - After using **dd** (or any similar utility) to write data to a raw removable block device, I would recommend running **sudo sync**, to flush any pending I/O, before actually unplugging it. Since you won't be writing to a filesystem (ie something you can unmount), you'll need to manually flush your buffers to ensure a clean write.

---

### Post by solarwind on 2008-03-19
> **kidders said:**
> Yep, it ought to. I suppose you could maybe gzip the result, so the blank space in the dump doesn't take up so much room. Anyhow, when you want to restore your disk to its original condition, you can just dump the data back onto it.

Two warnings, just in case you're not already aware of them...

1 - Make sure your USB disk is not in use while **dd** is running. Particularly when dumping your image back onto the device again, be sure no part of it is mounted, and try not to give your Linux any reason to probe its partition table, and so on.

2 - After using **dd** (or any similar utility) to write data to a raw removable block device, I would recommend running **sudo sync**, to flush any pending I/O, before actually unplugging it. Since you won't be writing to a filesystem (ie something you can unmount), you'll need to manually flush your buffers to ensure a clean write.

Very useful sync tip. Thanks!

---

