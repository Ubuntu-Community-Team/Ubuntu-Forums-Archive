---
title: "Automount Hard Drive Problem"
date: 2008-06-09
forum: General Help
---

### Post by Blind Tiger on 2008-06-09
** Please note.  This thread has been marked solved. **

Out of nowhere after 8 months running Gutsy, my ntfs partitions no longer automount.  I have looked at /etc/fstab and the output of sudo blkid.  All appears to be ok.  I have posted the results below and omitted any information not relevant to the partition in question.  I am considering deleting their respective entries from /etc/fstab and using ntfs-config utility to remount them.  Any advice would be greatly appreciated.

From /etc/fstab:
> # /dev/hda1
UUID=80D85563D855588C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=8E5C26FE5C26E127 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

From sudo blkid
> /dev/hda1: TYPE="ntfs" UUID="80D85563D855588C" 
/dev/hdb1: TYPE="ntfs" UUID="8E5C26FE5C26E127" LABEL="Wild Skies" 

From sudo fdisk -l
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfefdfefd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4aab

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        8423    67657716    7  HPFS/NTFS
Solaris

As one final note, I recently added this line to my /etc/fstab entries to enable usb support in WMware server for my XP Pro guest OS.
> # USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by ryanhaigh on 2008-06-09
You might want to try mounting it manually. I suspect that the system believes the ntfs disk may not have been unmounted cleanly and mounting manually will give you an error message to that effect. If you have windows reboot into that then back into ubuntu to see if it works.

---

### Post by Blind Tiger on 2008-06-09
ryanhaigh -- Thanks for the tip.  I had done a restart back into Ubuntu, but this did not correct the error.  Your suspicion was correct!  After I booted back into XP, then restarted and booted back into Ubuntu, my drives were correctly mounted and displayed on the desktop as usual.

I suspect the unclean dismounting was due primarily from the intense gaming session I had earlier today while playing Portal and TF2.

---

