---
title: "Kernel Panic !!!!"
date: 2007-06-10
forum: General Help
---

### Post by luckyd on 2007-06-10
Today I tried to boot up and saw this 
> [ 26.388700] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
[ 26.388710] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[ 32.081346] RAMDISK: Ran out of compressed data
[ 32.081539] invalid compressed format (err=1)
[ 32.082668] Kernel panic - not syncing : VFS: Unable to mount root fs on unknown-block(0,0)
[ 32.088495] _

What do I do, this is my first kernel panic? :cry:

---

### Post by HereInOz on 2007-06-10
Not good with Kernel Panics either, but they are often related to hardware issues.  If you have the ability to change your RAM, do so, as Kernel Panics are sometimes RAM related.

---

### Post by AusIV4 on 2007-06-10
> **HereInOz said:**
> Not good with Kernel Panics either, but they are often related to hardware issues.  If you have the ability to change your RAM, do so, as Kernel Panics are sometimes RAM related.
This can be easily tested by using the memtest+ on the grub menu. If it turns out there is a problem with a few segments of memory, I believe there is a way to get some files that can be used by a special kernel module to ignore certain segments of RAM so it's still usable. I won't be any help with that regard, but memtest can definitely tell you if it's a RAM problem.

---

### Post by luckyd on 2007-06-10
Does yaboot have memtest?

---

### Post by luckyd on 2007-06-11
There is more weirdness to this story, when I ran os x off my external harddrive through my computer and ran memtest it said all of the memory was ok. So, im guessing this is a kernel problem... does anyone have a fix?

---

### Post by reidms on 2007-06-11
A friend of mine had kernel panics, and it turned out to be segmentation faults

---

### Post by luckyd on 2007-06-11
Yah, I forgot the only thing software installation that I remeber doing on the last successful boot was updating so kernel headers. So if anyone knows that that is the problem, and fixed it please help. My computer still won't boot :(

---

### Post by luckyd on 2007-06-11
Would bump ing up my ram do the trick ;)

---

### Post by antonc on 2007-06-12
Hmm.

Possibility that your initrd is corrupt or something related.
Did you do a kernel-image update or something similar before this?




> **luckyd said:**
> Today I tried to boot up and saw this 


What do I do, this is my first kernel panic? :cry:

---

### Post by luckyd on 2007-06-12
No, I just let the update manager do its default updates, but I guesss it is possible that it updated the kernel-image.

---

### Post by ]Nbx*cmD[ on 2007-06-18
Just for the record, the way to limit your ram amount is by using the flag *mem=XXXM* as a kernel option.

Anyhow, to be able to use a screwed up memory by limiting it, you should have been very lucky, cos if the broken segment is at the beggining of the ram then you'll have to be using your computer with like 4 RAM Mb... which is not possible, by the way ;)

So, my solution was getting a new RAM module :'(

---

