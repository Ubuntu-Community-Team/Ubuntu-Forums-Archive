---
title: "fs &quot;not clean&quot; after partition resize"
date: 2006-10-28
forum: General Help
---

### Post by candtalan on 2006-10-28
I have a demo PC with several distros and data partitions, Kubuntu(6.06) is in /dev/hda9 originally 4 GB with an adjacent 4GB (higher) partiton which I did not need (/dev/hda10 as it happens). 

Rightly or wrongly, I deleted hda10 and resized hda9 to 8GB using gparted.
If you are still with me, and smiling, I hope you can help...... :-)

(I do have other distros on the PC so I can get to hda9 sort of easily, its data can still be seen)

When booting into hda9 Kubuntu now, all goes well until the file system check when 'not clean' is declared, and I am invited to use either ctrl-D to continue regardless or enter root password for manual repairs.

If I use ctrl-D then the kubuntu seems to work normally.

Using the root password and e2fsck, and following warning about mounted partiton, I used umount /dev/hda9, then e2fsck. I do not say I know much about what I am doing... but anyway (it is not a totally crucuial system, and data is in another partition) - it seems to be worth trying to get straight again.

From another distro on the PC I also used e2fsck on /dev/hda9, and fdisk, and tune2fs -l /dev/hda9.
 When resize2fs is used, it reports that there is 'nothing to do', even with -f force option.

So I am even more floundering just now, what is my best next action please?
tia
alan c

---

### Post by candtalan on 2006-10-28
phew! solved it. For the record:
I can now see (I think) that this escapade had two stages after the gparted partiton deleted and resize of another. 
1) I saw a 'bad superblock probable' type of comment. I then sort of stumbled around with e2fsck repairs and similar, which I guess did the trick in the partition filesystem.
2) I did though continue to have perstistent 'not clean' comments at the final stages of booting up. (I confused these wrongly with e2fsck type errors). They seemed to be caused by an entry in fstab file of a (now) missing partition. The errors ceased when I #'d out the particular entry. The partition numbering above the deleted one had changed when I deleted a partition (I know now...).

---

