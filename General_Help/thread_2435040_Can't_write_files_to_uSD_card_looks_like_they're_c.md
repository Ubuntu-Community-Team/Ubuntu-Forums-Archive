---
title: "Can't write files to uSD card: looks like they're created but gone when remounted"
date: 2020-01-15
forum: General Help
---

### Post by ldmoretti on 2020-01-15
I can't seem to create files on my uSD card. No error is given and it  looks like the file is there until I unmount and remount the filesystem  and then everything is gone.

  Simplest steps to recreate:

  
[LIST]
[*]Insert uSD card in port
[*]cd to mount point (/media/$USER/6139-3562)
[*]touch test.txt
[*]ls (lists test.txt)
[*]cd ..
[*]umount 6139-3562 (unmounts successfully)
[*]reinsert card
[*]cd 6139-3562
[*]ls (no test.txt listed, other prexisting files are there)
[/LIST]

 fdisk output:

  ```
Disk /dev/mmcblk0: 59.49 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device         Boot Start       End   Sectors  Size Id Type
/dev/mmcblk0p1      32768 124735487 124702720 59.5G  7 HPFS/NTFS/exFAT
     

```

---

### Post by sudodus on 2020-01-15
What happens if you flush the buffers manually with 'sync' before unmounting? (It should not be necessary, but maybe the linux support for exfat is flaky, so you could try that),

You could also try with a file with real content, for example

```

echo Hello > hello.txt
cat hello.txt                # check that the content is there
sync

```

Unmount, unplug, and plug in again ...

If there are still problems, maybe the drive is failing - gridlocked (looks like it accepts write commands, but it is really read-only). See [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) for more details.

---

### Post by ldmoretti on 2020-01-15
Thank you for your reply:
After further investigation it seems to be a problem with the particular SD card.

---

