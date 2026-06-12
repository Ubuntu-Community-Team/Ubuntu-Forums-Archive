---
title: "Backups and dual-boot systems"
date: 2008-01-14
forum: General Help
---

### Post by rockin_goliath on 2008-01-14
I am trying to find *my* perfect backup scheme. For my purposes, Sbackup comes pretty close, but there are some limitations to it. Ideally, I would like it to be able to preserve file permisions/owners/groups, but my biggest question is IS IT ABLE TO BACKUP THE CONTENTS OF MY WINDOWS PARTITION AND RESTORE IT FAITHFULLY IN THE EVENT OF A TOTAL SYSTEM FAILURE, SUCH AS A BUSTED HARD DRIVE? Does anyone know if this is possible? I looked into NotSoSimpleBackup, but the website was in a language I don't understand.

---

### Post by capink on 2008-01-14
The only way to backup windows as far as I know is to use disk or partition cloning software like [partimage]("http://www.partimage.org/").

I use partimage to backup my windows partition which is formatted as FAT32. Last time I checked partimage page they said NTFS support is not complete. There are other commercial alternative like norton disk if you not able to backup NTFS drives.

Here is a guide on using [partimage]("http://www.psychocats.net/ubuntu/partimage")

Backing up linux is easier. I used to back it up with partimage. But now I back it up with tar (which preserve permissions and ownership). The advantage to tar is that I can format my partition to another filesystem ( e.g xfs ) and resotre my backup. Resotring from cloning software you cannot change the filesystem type.

To backup you linux system using tar

```
sudo tar cvzpf /path/to/backup/file.tar.gz --one-file-system --exclude=/proc/* --exclude=/dev/* --exclude=/tmp/* --exclude=/sys/* /
```

If you are saving the backup file on the linux root partition ( which is not recommended) you have to exclude it ( add the option --exclude=/path/to/tar).

--one-filesystem option means that any other partitions mount on root will not be backed up. so if you have separate partition for home append /home to the end of the previous command/


to restore your system from tarball:

1. Mount the root partition on any mount point you want (from a live cd or sysrescue cd)

```
sudo mount -t ext3 /dev/sdxy /mnt
```

2. (Optional) Delete contents of your mounted root partition:

```
sudo rm -r /mnt/*
```

3. Restore from the tar file ( you have to mount the partition that contains the tar archive ):

```
sudo tar xvpf /path/to/tar.archive --same-owner -C /mnt
```


Replace /mnt in all the above commands with the mount point of your choice.


Edit: If you ever decided to change the filesystem type of the root partition, you will have to replace the old UUID of the root in both /etc/fstab/ and /boot/grub/menu.lst with the new one.

---

