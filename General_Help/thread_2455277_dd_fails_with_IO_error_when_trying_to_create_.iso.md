---
title: "dd fails with I/O error when trying to create .iso"
date: 2020-12-16
forum: General Help
---

### Post by jcdenton1995 on 2020-12-16
Hello all!

Obligatory I am not a pirate!

I'm trying to create an .iso image of an old game cd but when I run 'dd' the cd drive sounds like it's dying a miserable death and then the copy fails...```
dd if=/dev/sr0 of=game.iso bs=2048
```

The game is Freelancer if anyone is wondering, and it is mine, I paid about £5 for it on eBay. The thing is my PC doesn't have a disk drive but my old laptop does, so I'm trying to get an .iso going so I can transfer it to my PC and play it. Could it be that the disk is write protected? or is it an error on my part?

I have another old game disk that copies fine using dd, so I'm guessing it's not the laptops CD drive, although it's not conclusive.

Any advice is appreciated

---

### Post by dinkidonk on 2020-12-16
The CD may have some sort of copy protection preventing it from being read like you want to. Another thing is that you have set "game.iso" to be created in the working directory which may be in a write protected area. I'd suggest to use a more restrictive path, like "~/game.iso" or whatever.

---

### Post by SeijiSensei on 2020-12-16
When does the copy fail? Right away or later? Could it be a disk space problem? What is the actual error message you receive?

---

### Post by Impavidus on 2020-12-16
When you create the .iso, you only read the optical disk, not write it. And it's meant to be read, or it would be useless. Copy protection works when the optical disk drive has an anti-feature to recognise the copy-protect code and refuses to burn if that's present.

It sounds like a low-level read error. If the disk drive is OK, it's probably the disk. Maybe cleaning the disk helps.

---

### Post by The Cog on 2020-12-16
Many old games CDs had deliberately introduced errors on the disk so that they could not be copied in the normal way. I think the games would often check that certain sectors were unreadable with I/O errors before they would play. Reproducing disks with I/O errors is very difficult. It sounds to me as though you have one of those.

---

### Post by QIII on 2020-12-16
If you are going to use dd for this, I would try something similar to the following and specify the destination

```
dd if=/dev/sr0 of=/path_to/destination_dir bs=2048
```

---

### Post by #&amp;thj^% on 2020-12-16
Just my 2 cents, If there are read errors while reading the source, "conv=sync,noerror" is necessary to prevent dd from stopping on error and performing a dump.

---

### Post by jcdenton1995 on 2020-12-17
> **dinkidonk said:**
> The CD may have some sort of copy protection preventing it from being read like you want to. Another thing is that you have set "game.iso" to be created in the working directory which may be in a write protected area. I'd suggest to use a more restrictive path, like "~/game.iso" or whatever.

Sorry my bad, when I wrote "of=game.iso" what I actually meant was "/path/to/game.iso" but your right, a good point.

> **SeijiSensei said:**
> When does the copy fail? Right away or later? Could it be a disk space problem? What is the actual error message you receive?

It fails immediately, the drive spins up and then drops to a really low rpm while making erratic drive noises. I don't think it's a disk space problem as the laptop only has a minimal ubuntu 20.04 install and very little else, and from memory it's got a 512 GB drive. The actual output from 'dd' is below...```
dd: error reading '/dev/sr0': Input/output error
844+0 records in
844+0 records out
1728512 bytes (1.7 MB, 1.6 MiB) copied, 25.3084 s, 68.3 kB/s
```...pretty vauge, I looked through the info page to see if there is a way to get more detailed debug information but I can't see anything.

> **1fallen said:**
> Just my 2 cents, If there are read errors while reading the source, "conv=sync,noerror" is necessary to prevent dd from stopping on error and performing a dump.

I tried this after you suggested it, and while the process does continue, the drive still makes the same crazy noises mentioned above, and it writes around 50 KiB/s. Even if I left it for a very long time I think the resulting file would be junk :/

---

### Post by TheFu on 2020-12-17
This would be where I used **ddrescue** instead of dd.

Sometimes ebay purchases aren't the best. I've bought some used games from local used game/cd/dvd stores and about 1:20 doesn't work. That's the chance we take.  I'll keep doing it too. The risk-reward is acceptable to me.

---

### Post by jcdenton1995 on 2020-12-17
The thing is the game plays fine on a windows machine, just wont let me copy the disk, the same with a copy of Max Payne 1 that I have, plays fine but dd fails immediately. The impression I'm getting from reading these replies is that it's not totally common for that to happen and it *may *be some reason other than copy protection...

---

### Post by sudodus on 2020-12-17
When the game plays fine on a Windows machine, but you cannot copy it, I suspect that there is copy protection by means of some bad sectors or something else put there in order to prevent copying. There is probably not much you can do if you want to use legal tools/methods (and I won't recommend illegal methods).

---

### Post by dinkidonk on 2020-12-17
> **jcdenton1995 said:**
> I tried this after you suggested it, and while the process does continue, the drive still makes the same crazy noises mentioned above, and it writes around 50 KiB/s. Even if I left it for a very long time I think the resulting file would be junk :/

I would still try to let it complete and evaluate the result rather than guesstimating the outcome.

---

### Post by jcdenton1995 on 2020-12-19
I agree, but at the rate it's copying it would take days, weeks even maybe! I'd like to get it going but I'm not that bothered. But also on the other hand I probably will because I never use the laptop these days so I have the time. If I do I'll update this thread with my findings.

---

### Post by TheFu on 2020-12-19
> **jcdenton1995 said:**
> I agree, but at the rate it's copying it would take days, weeks even maybe! I'd like to get it going but I'm not that bothered. But also on the other hand I probably will because I never use the laptop these days so I have the time. If I do I'll update this thread with my findings.

ddrescue does multiple attempts of the source, but it will continue to the next sector if there is a failure. There are options to limit how hard it tries to recover failing sectors and with the log file, we can have it re-run after it finishes the first attempt of the entire disc.  Failures will always slow down clones like this, but a typical DVD should be cloned in 2 hrs or less.

---

