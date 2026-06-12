---
title: "Move existing home directory to new install?"
date: 2016-12-01
forum: General Help
---

### Post by Macamba on 2016-12-01
My MBR got corrupted, and so my bootloader went missing. Instead getting back the bootloader for the old system (14.04 LST) I thought it opportune to install the new version (16.04.1 LST). And that went wrong. The installation hanged. I rebooted after 5 minutes of inactivity. That resulted in all my settings being forgotten. Now I need to get everything working again. One important thing is that I need to connect my old home directory to my new installation, and subsequent new home directory. How do I accomplish that?

---

### Post by kingneutron on 2016-12-01
--If you still have the ISO, I would reinstall 14.04 again (or just download the netinstall.)  During Xubuntu 14.04 install in a VM, I was able to hit Ctrl+Alt+F2 and issue:
' sudo fdisk -l '  # determine partitions
' sudo blkid ' # list partition labels/UUIDs

--As long as you can remember or determine what your home partition was, you can point the installer to it during partition setup and tell it DO NOT FORMAT, use as /home.

--If you need more diagnosis to find /home during install - Hit Ctrl+Alt+F2
' sudo su - ' # become root, save typing
' fdisk -l '
' blkid '
' mkdir -pv /mnt/tmp '

STEP1:
' mount /dev/sda1 /mnt/tmp -oro ' # mount a partition read-only
' ls -al /mnt/tmp ' # Does the contents look like /home?  If so, then remember
' umount /mnt/tmp ' # CRITICAL STEP
( use sda2,etc and redo STEP1 )

--Once you have found /home partition AND UNMOUNTED IT, return to installer by hitting Alt+F7.

--Remember, BACKUPS are your friend - I hope you have at least /etc backed up somewhere...

---

### Post by Macamba on 2016-12-01
Thanks. That seems a solution to my current problem too. Can I reinstall 16.04 and do the same trick? I know what partition my home directory is on.

---

### Post by oldfred on 2016-12-01
Just to clarify.
Was /home on a separate partition before. If so just use Something Else to install. If you have backed up list of installed apps to make it easy to reinstall and any manual changes to system configuration that are stored in /etc, you can just select same / (root) partition. But when you select /home partition you must NOT select format or else it will get erased.

But if /home is inside the old install it needs to be separately backed up and/or moved to a separate partition first.

---

### Post by Macamba on 2016-12-02
Reinstall was the solution. Thanks.

---

