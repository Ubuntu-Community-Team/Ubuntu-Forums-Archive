---
title: "Strange SD Card problem"
date: 2017-01-06
forum: General Help
---

### Post by bcliburn on 2017-01-06
I'm having a rather strange problem with an SD Card, 
All programs I run to repair the card (fsck, e2fsck, disk program, Gparted) 
tell me ALL of the Superblocks are bad but the card reads just fine.
I can use it to boot a Raspberry Pi and everything runs just fine (is this normal for a corrupted card?)

Is there any other tools I can use to repair this?

(It's a Samsung 16GB Class10 Micro SD Card)

Thanks for any help in advance

---

### Post by kpatz on 2017-01-06
Maybe it's not corrupted but is formatted with something like FAT32 which fsck doesn't recognize?

If you have a Windows system, run a chkdsk on it.  Or install dosfstools and run dosfsck on it from Linux.

---

### Post by bcliburn on 2017-01-06
I'll Try that, I should have mentioned I've only used linux programs so far.
I can try it on my kids computer. I'll update if that works
Thanks!

---

### Post by sudodus on 2017-01-06
"If it ain't broke, don't fix it."

The card boots a Raspberry Pi and everything runs just fine. I think the problem is that the tools don't understands the structure of the card, the partition table or file system or both.

---

### Post by bcliburn on 2017-01-07
I probably should have mentioned that I could not write to the card. Sorry about that.
I've tried every program I could find on Windows and Linux and they all say that the card is write protected (it is absolutely not)
I guess that card is just fried somehow, but it's strange that I can still read from it.

Thanks for the help!

---

### Post by lisati on 2017-01-07
Some cards have a write-protect switch on them. With the label side up, and the contacts pointing away from you, take a look on the left. This is illustrated [here]("http://kb.sandisk.com/app/answers/detail/a_id/1102/~/sd%2Fsdhc%2Fsdxc-memory-card-is-write-protected-or-locked").

---

### Post by bcliburn on 2017-01-07
It's a Micro SD Card but I've checked the write protect tab on the adapters.
I've tried 3 different adapters 3 separate card readers on 2 different computers to make sure.
At this point I'm just gonna say the card is fried, I've got extras
Thanks for everyone's help.

---

### Post by DuckHook on 2017-01-07
SD Cards will only sustain a certain number of writes, after which they become read only. A common point of failure is the superblock, which seems to be your experience.

I had a very similar situation just two days ago&#8230;

In my case, the card in question was used for torrenting, which does a significant amount of writing to the superblock and continues to do so even after the torrent is completed, if you let it seed (like you're supposed to as a good member of the community). I'm not familiar with all of the details, but this is my understanding: unlike regular data, wear-levelling for the superblock is not spread over the whole card, but is confined to a certain area. If this area keeps getting written to, it will eventually reach write-lock, usually in the middle of a write, hence a corrupted superblock.

The above is just an educated guess. Your situation may be quite different than mine. In any case, a card with an unwritable superblock is useless except as a very high capacity quasi-DVD: it still holds all info that it had pre-freeze, but can never be written to again.

When you install your new card, you may wish to limit your writes to the superblock if possible. The worst culprits are apps that write access times. I found that the noatime parameter in fstab is useful, but not for torrents, which write to the superblock differently.

---

### Post by sudodus on 2017-01-08
+1 to DuckHook's explanation.

---

### Post by bcliburn on 2017-01-08
That sounds like that's exactly what is happening, I was running a Raspberry Pi from it.  What I've done now is just boot from the SD Card and run things on an external HD.  At least I know what happened now.

---

