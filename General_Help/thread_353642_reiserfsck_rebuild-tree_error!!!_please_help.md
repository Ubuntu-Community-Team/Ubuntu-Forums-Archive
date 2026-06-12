---
title: "reiserfsck rebuild-tree error!!! please help"
date: 2007-02-04
forum: General Help
---

### Post by jms830 on 2007-02-04
help!! I've made a grave mistake. I booted my computer and couldn't log into X. I realize now that it was b/c I ran out of disk space on my /home partition.  However, I didn't know that then, and so I ran a live CD and ran **sudo reiserfsck --scan-whole-partition --rebuild-tree /dev/hda2** and I got an error about being out of disk space. Then I realized the problem. So I rebooted, and Grub gave me an error 16 which is for a corrupt filesystem. I rebooted into the live cd and ran **reiserfsck** on my /dev/hda2 which is the drive. This is the output I get:

```

###########
Replaying journal..
Reiserfs journal '/dev/hda2' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..

Bad root block 0. (--rebuild-tree did not complete)

Aborted (core dumped)
```


AND then when I try to run that previous rebuild-tree command again, I get the same out of disk space error and it cannot complete!!! That error looks like this:

```
Reiserfs journal '/dev/hda2' in blocks [18..8211]: 0 transactions replayed
###########
reiserfsck --rebuild-tree started at Sun Feb  4 23:33:38 2007
###########

Pass 0:
####### Pass 0 #######
The whole partition (1953904 blocks) is to be scanned
Skipping 8270 blocks (super block, journal, bitmaps) 1945634 blocks will be read
0%....20%....40%....60%....80%block 1588026: The number of items (2) is incorrect, should be (1) - corrected
block 1588026: The free space (0) is incorrect, should be (2000) - corrected
pass0: vpf-10110: block 1588026, item (0): Unknown item type found [2478066440 91057 0x15e00 ??? (15)] - deleted
....100%                       left 0, 10574 /sec
207025 directory entries were hashed with "r5" hash.
        "r5" hash is selected
Flushing..finished
        Read blocks (but not data blocks) 1945634
                Leaves among those 10216
                        - leaves all contents of which could not be saved and deleted 2
                Objectids found 206718

Pass 1 (will try to insert 10214 leaves):
####### Pass 1 #######
Looking for allocable blocks .. finished
0%....20%....40%....60%....80%....100%                         left 0, 567 /sec
Flushing..finished
        10214 leaves read
                10028 inserted
                186 not inserted
####### Pass 2 #######

Pass 2:
0%..Not enough allocable blocks, checking bitmap...there are 0 allocable blocks, btw

out of disk space
Aborted (core dumped)
```

Please help me! What can I do??

---

### Post by jms830 on 2007-02-06
Turns out there was a bug in reiserfsckprogs 3.6.19. Download reiserfsckprogs 3.6.20 and install from source, then ran it again. Unfortunately, my data was still lost. I don't understand how it happened, but somehow, my hda2 got copied onto my hdb1 and then when i restored hdb1, it was all the stuff from hda2. Strange, and unfortunate for me b/c I seem to have lost everything from hdb1.

---

