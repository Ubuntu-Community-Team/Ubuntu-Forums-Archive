---
title: "Format SD card"
date: 2023-10-24
forum: General Help
---

### Post by John Jason Jordan on 2023-10-24
I have a brand new 1TB SD card. When I first inserted it into the computer it was automatically mounted and appeared to be working fine. However, it was formatted exFAT, which I didn't really want, so I fired up GParted and proceeded to remove the partition, recreate it, and format it as ext4, with the label 1TB-SD. The operations completed without error, but it could not be mounted, with the error 'missing codepage or helper program, or other error.'

I closed GParted and ran Gnome Disk Utility, which offered 'check filesystem,' 'repair filesystem,' and 'format,' among other options. I started with 'check,' but it gave the same error message as above. 'Repair' completed without error, but it still could not be mounted, giving the same error message. Finally, still in Gnome Disk Utility, I reformatted it as exFAT and reapplied the label. After that it could be mounted and functioned normally.

Still not happy I decided to move to the command line. This is what happened there:

```

sudo mkfs.ext4 -L "1TB-SD" /dev/mmcblk0
mke2fs 1.47.0 (5-Feb-2023)
Found a dos partition table in /dev/mmcblk0
Proceed anyway? (y,N) y
Discarding device blocks: done                            
Creating filesystem with 262144000 4k blocks and 65664000 inodes
Filesystem UUID: 735301d6-e49f-4aa8-9222-8f621f57f7e1
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632,
2654208, 4096000, 7962624, 11239424, 20480000, 23887872, 71663616,
78675968, 102400000, 214990848
Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done     

$ sudo mkdir /media/jjj/1TB-SD
$ sudo mount /dev/mmcblk0 /media/jjj/1TB-SD 
mount: /media/jjj/1TB-SD:
wrong fs type, bad option, bad superblock on /dev/mmcblk0, missing
codepage or helper program, or other error. dmesg(1) may have more
information after failed mount system call.

$sudo dmesg <sorry, hard to read this below>
[442690.762650] EXT4-fs error (device mmcblk0p1): ext4_find_extent:936: inode #8: comm pool-udisksd: pblk 131104767 bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0) [442690.764359]
EXT4-fs (mmcblk0p1): Remounting filesystem read-only [442690.764363] jbd2_journal_init_inode: Cannot locate journal superblock [442690.764365] EXT4-fs (mmcblk0p1): Could not load journal inode
[445844.987215] EXT4-fs error (device mmcblk0): ext4_find_extent:936: inode #8: comm mount: pblk 131104767 bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0) [445845.991577]
jbd2_journal_init_inode: Cannot locate journal superblock [445845.991592] EXT4-fs (mmcblk0): Could not load journal inode [445897.081747] EXT4-fs error (device mmcblk0): ext4_find_extent:936: inode #8: comm pool-udisksd: pblk 131104767 bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0) [445897.083607] EXT4-fs (mmcblk0): Remounting filesystem read-only [445897.083627]
jbd2_journal_init_inode: Cannot locate journal superblock [445897.083633] EXT4-fs (mmcblk0): Could not load journal inode

```
Is it possible that the device was somehow manufactured so that it can only be formatted exFAT? I could use some clues. Maybe someone can figure out what the dmesg results above mean. :)

---

### Post by MAFoElffen on 2023-10-25
First please use CODE Tags when posting commands and output on the Forum, that will keep you out of troubles with the Moderators. Refer to the Posting Guidelines: #3, and Code Tags links in my signature line.

On SD types of storage cards, do
```

sudo mke2fs -t ext4 -O ^has_journal -L 1TB-SD /dev/mmcblk0

```
SD types of cards do not do well with journals. That option will format the card to ext4 without a journal being created.

---

### Post by John Jason Jordan on 2023-10-25
> **MAFoElffen said:**
> 
On SD types of storage cards, do
```

sudo mke2fs -t ext4 -O ^has_journal -L 1TB-SD /dev/mmcblk0

```
SD types of cards do not do well with journals. That option will format the card to ext4 without a journal being created.

Many thanks. That did the job! :)

---

### Post by HermanAB on 2023-10-25
I have seen this too - some SD cards and USB widgets work with NTFS and Ext4 with journals and some don’t.  There is a little processor in there that manages the blocks and some are crummier than others and I don’t buy them often enough to know which to avoid.

---

