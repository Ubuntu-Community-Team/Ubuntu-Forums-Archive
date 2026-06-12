---
title: "Clonezilla GPT Conversion"
date: 2015-11-27
forum: General Help
---

### Post by Quarkrad on 2015-11-27
(Running 14.04).  I have a mbr HD that has multiple partitions (some within an extended/logical partition) that I would like to convert to a gpt HD.  If I clone my **30GB / **partition and **100GB /home** partition using Clonezilla, delete the HD and rebuild all my partitions using the gpt format (so I land up with a gpt HD), can reinstall my / and /home images back to the same size gpt partitions and it work as before?  Assuming I will have to re-install grub (the efi version that I'm not too sure about*).  * Is this something special or can you install grub on a gpt HD using boot-repair?

---

### Post by oldfred on 2015-11-27
Best not to.
You want to copy data, not clone.

You can clone an entire gpt drive, but  not its partitions as gpt partition tables & partitions have GUID's that must match. And MBR would not have any GUIDs.

If you format gpt & create partitions then you can just copy the data into those partitions. But if a / (root) partition you have to reinstall grub & must have either (or both) the ESP - efi system partition for UEFI boot or a bios_grub partition for grub to correctly install.

There are other settings if moving an install like, fstab, and the default where grub installs into. There may be some others depending on your configuration.

Often easier better to just do a new install to gpt drive, then copy all your data and /home into new install.

You can convert a MBR drive in place to gpt. I have not done it and you do need that good backup.
Still issues on new UUIDs & GUIDs.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

    
This user did do a copy with dd.
 Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by Quarkrad on 2015-11-27
Already backed up.  If I trash the whole disk, set my bios to *efi only* and build a multi partition table from scratch can I simply do an install of windows 10, followed by a clean install of 14.04 into a / partition and then a copy and paste my backup of  /home to the new /home partition and have a gpt HD?  Would doing a clean install of 14.04 install a gpt compliant version (if that is the right term) of grub2?

---

### Post by oldfred on 2015-11-27
I think it still is best to install Windows first.

Both Windows & Ubuntu will install to UEFI boot mode with gpt partitioning if you boot installer in UEFI mode. But if you boot in BIOS mode then it installs in BIOS mode.
Windows only boots from a gpt partitioned drive with UEFI.
Ubuntu can boot from gpt with either UEFI or BIOS, but best to keep UEFI as boot gets complicated. And UEFI, UEFI with secure boot and BIOS has added complications enough.

If partitioning in advance, Windows requires an extra partition or two.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Use Windows tools for Windows and Linux tools for Linux.

See also link in my signature for (too much) UEFI info. 
But you really need to at least review these:

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by Quarkrad on 2015-11-27
Sorted - thank you.

---

