---
title: "Need HELP! Deleted partitions requires data recovery!"
date: 2017-10-02
forum: General Help
---

### Post by derekcairo on 2017-10-02
I have a bit of an unusual case.

As I was trying to install a new flavor of Ubuntu I accidentally gdisk'd /dev/sda instead of /dev/sdc and deleted all of the partitions off my data drive. I also wrote to the device a new GPT partition table label with a 2G EFI partition and a Linux Filesystem partition that filled the rest of the disk. I later then deleted the two partitions and made an ext4 partition that filled the rest of the device. At this point forward I have done a complete dd backup of the 2TB drive and am working on the backed up identical drive (also 2TB). 

A friend on IRC was helping me through all of this in the process, others rightfully told me to backup next time, and I was also recommended Testdisk as well. I've used Testdisk unsuccessfully except it's photorec pacakage to to recovery millions of scattered files. While the data is all there I can not possibly make any use of it. My friend on IRC told me that as long as I did not mkfs the device I should be safe (which I did not). He also gave me a few bash scripts to brute-force mounting the device on various block sizes which failed unsuccessfully. E2fsck also failed to recover the device without a proper superblock backup block.

After trying numerous configurations for two days I remembered that I may have actually created just an ext4 filesystem on the device with an empty partition while using Gnome's Disk Utility tool. We then tried using a configuration which would have been for an empty partition table with an ext4 filesystem. "mount -o sb=32768 /dev/sdb /mnt" which succeeded! Unfortunately, once I entered directories 2 directories deep "ls" reported "Structure needs cleaning" errors for numerous files and directories. When I ran e2fsck I ended up salvaging only 29GiB of the original 1TiB of data as it cleared the data for example "Entry 'VBox' in / (2) has deleted/unused inode 84934657.  Clear<y>?".

So far this is as far as we have got. Does anyone have any ideas on how I could salvage the rest of the data?

Many Thanks!

---

