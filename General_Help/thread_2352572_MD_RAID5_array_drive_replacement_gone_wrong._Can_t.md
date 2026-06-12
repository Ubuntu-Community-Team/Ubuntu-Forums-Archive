---
title: "MD RAID5 array drive replacement gone wrong. Can this be fixed?"
date: 2017-02-13
forum: General Help
---

### Post by jeroen947042 on 2017-02-13
Hi,

I have been running a 4x1 TB drive md array in raid5 configuration for years, and decided it was time for a capacity upgrade to 4x2TB drives. The plan was to replace the drives one at a time marking a drive as failed, remove it from the array, replace with another drive, adding the new drive to the array and rebuilding the array (Repeat for each drive). However, something has gone haywire, and the array no longer works. I'm hoping someone can help me figure out what went wrong and/or how to fix it, if at all possible. Here's what I did in detail, and what happened:

1. mdadm --manage /dev/md0 --fail /dev/sdb1 --remove /dev/sdb1
2. Array reported as degraded, which is as expected
3. Power down, replace drive that was sdb with a new one, boot
4. mdadm --manage /dev/md0 --add /dev/sde
5. Array reported as clean, rebuilding 
6. After rebuilding everything looks normal, and works as expected. However, I realize I didn't partition the new drive and added the raw device. While this apparently works, it is also apparently not recommended. So:
7. mdadm --manage /dev/md0 --fail /dev/sde --remove /dev/sde
8. Array reported as degraded
9. sfdisk -d /dev/sdc | sfdisk /dev/sde (where sdc is one of the other 1 TB drives. I realize this means I won't increase capacity, but I figure I'll tackle that when I am back to a functioning array consisting of all 2TB drives)
10. mdadm --manage /dev/md0 --add /dev/sde1
11. Array reported as clean, rebuilding
12. When rebuilding finishes, all looks good, and everything seems to work. 
13. mdadm --detail /dev/md0 reports 4 good drives, including /dev/sde1

This is where things start to go wrong

13. mdadm --manage /dev/md0 --fail /dev/sdc1 --remove /dev/sdc1
14. Power down, replace drive that was sdc with a new one, boot
15. Array cannot be started, Ubuntu drops to emergency mode
16. mdadm --details /dev/md0 reports 3 drives, as expected, but instead of /dev/sde1 it once again shows /dev/sde, the raw device!
17. mdadm --assemble --scan -v says (approximately):
        mdadm: added /dev/sde to /dev/md0 as 0 (possibly out of date)
        mdadm: added /dev/sdb1 to /dev/md0 as 1 
        mdadm: added /dev/sdd1 to /dev/md0 as 2
        mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
18. After some googling, I decide to try: mdadm --assemble --scan --force
19. This _seems_ work, it reports the array starts, and I decide to add a 4th drive, which is already connected so I don't need to power-cycle
21. Array reported as clean, rebuilding.
22. Now rebuilding has finished, but and it lookd like it starts the md array, but it can not mount the filesystem. journalctl -xb shows (leaving out really long device id's):

systemd[1]: dev.....device: Dev dev-disk....device appeared twice with different sysfs paths
kernel: EXT4-fs (md0): mounting ext3 filesystem using the ext4 subsystem
kernel: EXT4-fs (md0): ext4_check_descriptors: Block bitmap for group 880 overlaps superblock
kernel: EXT4-fs (md0): ext4_check_descriptors: Block bitmap for group 880 not in group (block 0)!
kernel: EXT4-fs (md0): group descriptors corrupted!
mount[558]: mount: mount /dev/md0 on /mnt/bigdata failed: structure needs cleaning

So that's where I'm at right now. Is there anything to be salvaged here, or should I consider the data lost? If there is anything about the current state of the system that would be useful, just let me know.

Thanks in advance,

Jeroen

---

