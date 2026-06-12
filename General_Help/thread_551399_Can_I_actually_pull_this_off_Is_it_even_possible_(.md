---
title: "Can I actually pull this off? Is it even possible? (xtreme partition editing)"
date: 2007-09-15
forum: General Help
---

### Post by AstarothCY on 2007-09-15
This is my setup:

sda (500GB)
sda1: ubuntu root - ext3 - 50GB
sda2: ubuntu home - ext3 - 413GB
sda3: linux-swap - 2GB

sdb (80GB)
sdb1: winxp - ntfs - 80GB

I recently broke my installation by upgrading from Edgy to Feisty, and since I'm going to have to reinstall I thought I might as well do the smart thing and rearrange my partitions to make it more efficient. This is what I ideally want to end up with:

(I will swap the two hard disks around so the 80GB will be sda and the 500GB will be sdb)

sda (80GB)
sda1: ubuntu root - ext3 - 15GB
sda2: ubuntu home - ext3 - 30GB
sda3: linux-swap - 2GB
sda4: winxp - ntfs - 33GB

sdb (500GB)
sdb1: share - fat32 - 500GB

I think you can sort of tell what I'm trying to do here. I'm offloading all my data & media which is currently in ubuntu home and putting it on the big slow drive, in fat32 so that it is more easily accessible by winxp (yes i know about ext2fs). I am putting my OSs onto the 80GB, avoiding the annoying hd0/hd1 switcharound I have to put into grub in order to boot winxp (winxp needs to be sda1 so the switcharound fools it). And, finally of course I am maximizing the available space I have for data & media.


Now how exactly would I go about doing this, WITHOUT a backup drive? This is what I had in mind:
1. Resize ubuntu root to gain about 30GB free space.
2. Write a new fat32 share partition into the free space.
3. Move 30GB of data off ubuntu home into the share partition.
4. Shrink ubuntu home, enlarge share partition, move more data.
5. Repeat until all data is in share partition, leaving only apps in ubuntu home.
6. Format winxp partition, set up the partition table as above, install OSs, make sure everything works.
7. Finally, nuke the current ubuntu root and home partitions and the linux-swap, and enlarge the share partition to take up the whole drive.

Is this possible? I will love you forever if it is. If it is risky then please tell me exactly what the risks are so that I can do a risk assessment like a good scientist :D


EDIT:
Bah I just read that fat32 has a 4GB size limit, forget it, I'll keep my data on ext3 and use ext2 IFS. (It sucks being a noob.)

I suppose the new plan is a lot simpler:
1. Format the 80GB, install winxp/ubuntu.
2. Delete ubuntu root and linux-swap partitions off the 500GB.
3. Resize ubuntu home to take up entire drive, clean up all the app data to leave just documents & multimedia.

Still, out of curiosity, is what I asked earlier possible?

---

### Post by Sef on 2007-09-15
> sda3: linux-swap - 2GB

How much ram do you have?   Do you do movie editing, gaming or other ram intensive usage?  If not, then I would either have a 1 gb swap at the most, or eliminate it altogether.

---

### Post by AstarothCY on 2007-09-15
i have 1.5GB RAM and I do gaming and possibly some audio editing.. im not that concerned with gaining 1GB tbh, id rather have 2 and be on the safe side.

So yeah, is my revised plan ok? any gaping holes i've overlooked?

---

### Post by Sef on 2007-09-15
> I suppose the new plan is a lot simpler:
1. Format the 80GB, install winxp/ubuntu.
2. Delete ubuntu root and linux-swap partitions off the 500GB.
3. Resize ubuntu home to take up entire drive, clean up all the app data to leave just documents & multimedia.


It seems ok.  Just **back up** your data before doing the changes.

---

### Post by brandonjp on 2007-09-16
Just wanted to throw in a comment that my setup is very similar to yours.  I've been running it that way for almost a year with no problems at all.  I'd particularly like to praise the Ext2 IFS driver from fs-driver.org for doing such a great job.  I've got all my data, media, docs, etc on a very large ext3 partition called the TANK and both Windows and Ubuntu have done a fine job of reading and writing to the TANK.  I do a LOT of audio recording and video editing straight to and from that ext3 drive from within Windows and have (so far) not had a single problem, crash or otherwise (yet!) (and I hope not ever) (please, God, no!).  But I agree you should back up your important stuff before and even after on a regular basis.

I have, however, wondered if Windows will eventually cause me problems by fragmenting files on the ext3 drive - to my knowledge there's no way to defrag an ext2/3 drive - maybe I'll post about that in another thread.

good luck!
--bp

---

