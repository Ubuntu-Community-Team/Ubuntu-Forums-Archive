---
title: "ZFS: Move rpool to different zpool after install?"
date: 2023-06-26
forum: General Help
---

### Post by oguruma1218 on 2023-06-26
I have a machine running Ubuntu 22.04LTS. It's installed with ZFS on a single drive. I'd like to move the rpool to a new pool that consists of a 3 NVMe SSDs in RAIDZ1. I'm ambivalent as to whether or not the boot pool stays on its current drive or moves to the RAIDZ pool. 

Is this feasible to do after Ubuntu is already installed?

---

### Post by MAFoElffen on 2023-06-27
Since you are familiar with that OpenZFS ZFS-On-Root install guide, I'll tailor this to what they used there.

A ZFS pool is a container that is initialized on a disk or in a partition. You can move a pool easily to another disk if you were keeping the same type of zpool type, if it were a normal pool, on a disk that is other-than a root disk... but it is a root disk. If it were an additional disk, yuo would just export the pool, then import it to the new system root (disk).

With ZFS, you can migrate it to larger disks on the same system in a more flexible, intelligent fashion. If you were going to just migrate to a larger disk with an 'alike' type of pool, you would add the new pool partition to pool, with the zpool autoexpand property set to on, which would expand and include the new partition into the pool, then use zpool replace to move the data off the old partition to the new partition and remove the old partition out of the pool... But that won't work with single disk pools to RAIDz pools... It can't transform pool types.

If it were other than a root pool, on a differing pool type (single disk to mirror, single disk to RAIDz, RAIDz2 to RAIDz3...) then what I do, is create the new pool (with the right mounts that I want it to end up with after I am through) and import / attach the new pool with a different name, to the same system... Abstract like this example
```

zpool create [options] mountpoint=/home -R /home2 homepool2

```
Then recreate any datasets that were in the old pool... So that the datasets and directory structure is the same between them... Then rsync between the two. Then export both the old pool, and the new pool. Then import the new pool to the right mountpoint, with a new name in this format:
```

sudo zpool import homepool2 homepool

```
Then to make the name permanent, export and import it again...

But you are wanting to replace a root disk onto an other than same pool type, so we have to build on that combined process...

So what I would do to migrate a ZFS-On-Root system installed on a root disk, is to connect the new disk to the system. Then I create the new directory structure on the new disk (you have already). Then create the new pools, mounted temporarily to /mnt (-R flag). I recreate the datasets within the pools. The rsync between the old rpool to the new RAIDz rpool mounted in /mnt. Do the same from the old bpool to the new bpool mounted in /mnt... Same for the bpool and the EFI partion. The use the rest of the mount instruction from the github ZFS install instructions to chroot into the new system.   

The only thing that you will need to do from there, is to int your new swap...
```

mkswap -f ${DISK}-part2

```
...update the /etc/fstab file to the new UUID's
```

echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part1) \
    /boot/efi vfat defaults 0 0 >> /etc/fstab
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part2) \
    none swap discard 0 0 >> /etc/fstab

```
Mount everything, verifying the wirng is good
```

zfs mount -a
mount -a

```
Then reinstall Grub2, and configure Grub
```

apt install --yes --reinstall grub-efi-amd64 grub-efi-amd64-signed linux-image-generic shim-signed
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
update-initramfs -c -k all
update-grub

```
Then exit the chroot, unmount the filesystem safely, and reboot...
```

exit
sudo mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | xargs -i{} umount -lf {}
sudo zpool export -a
sudo shutdown -P now

```
Disconnect the old disk. Boot and test.

The safe thing is that if it fails, nothing has changed on the old disk. If need be, you could just change the old disks back to how they were and it will come back up, (temp) mount and chroot into the new disk, to make any further needed changes, again without changing anything on the original disks and pools.

You'll find that RAIDz pools are a lot faster performance than single disks. If you read though this thread: [https://ubuntuforums.org/showthread.php?t=2486010&highlight=zfs+raidz3](https://ubuntuforums.org/showthread.php?t=2486010&highlight=zfs+raidz3) 
You'll see where I led someone through steps to fine-tune RAIDz pools for performance. I also posted steps there to create L2ARC ad SLOG pool caches, benchmarking, etc.

Also note from that thread that I use much more than one disk in my server-- There are 13 disks in that server. (SSD x 6, NVMe x 7) I segment out my home and data pools out so they are easier to migrate to a newer system or such.  I keep my root disk as a single disk, then attach my other important pools as RAIDz2. That way if there is a problem, things are more isolated and easier to fix, or to move around data.

To give you an idea of the throughput on just the slower SSD RAIDz Pool:
```

root@Mikes-B460M:/home/mafoelffen# zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub in progress since Tue Jun 27 05:05:54 2023
    1.55T scanned at 3.56G/s, 813G issued at 1.82G/s, 1.55T total
    0B repaired, 51.12% done, 00:07:07 to go
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors
root@Mikes-B460M:/home/mafoelffen# zpool iostat datapool
              capacity     operations     bandwidth 
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
datapool    1.55T  7.54T     20     41  1.59M  1.29M

```

---

