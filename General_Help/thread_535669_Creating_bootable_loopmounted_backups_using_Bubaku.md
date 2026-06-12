---
title: "Creating bootable loopmounted backups using Bubakup (For standard Ubuntu not Wubi)"
date: 2007-08-26
forum: General Help
---

### Post by tuxcantfly on 2007-08-26
**New guide at [http://ubuntuforums.org/showthread.php?t=535684](http://ubuntuforums.org/showthread.php?t=535684)**

Note that this guide is designed for users running standard Ubuntu, not for Wubi users. It is posted here on the Wubi Forums as a temporary solution until the guide is approved in the howtos section, and also since it makes use of the same loopmounting technology as Wubi does.
[B][I]
Main site, and a screenshot-based guide is at [http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html)[/I][/B]

**Introduction**

Bubakup, the Bootable Ubuntu Backup, is a tool that allows you to create a bootable backup image of your running system. It supports creating uncompressed, bootable loopmounted disk images of the whole or parts of the system, deleting backup disk images, archiving backup disk images using 7-zip, restoring backed-up archived disk images, and LVPM (which is pre-installed in the generated disk images) can be used to restore the backup loopmounted disk image to an actual partition.

**Usage Cases**

The bootable disk images created by Bubakup can be used as an emergency recovery and restoration tool, should your primary system become unbootable. It can also be used as a sandbox environment for testing bleeding-edge and unstable code, in an environment that is the same as though you were using your primary system, without harming your primary system. It can also be used as a general full system and data backup/restoration utility.

**What it does**

A loopmounted disk image of the size selected by the user is created on the partition selected by the user, and the contents of the currently running root partition, excluding directories selected by the user, are copied into it. The loopmounted disk image is then patched and modified with loopmounting patches to allow it to boot. A menu entry is then added to grub allowing for the booting of the loopmounted disk image. The user can then reboot into the bootable backup disk image and restore it to a partition using LVPM, archive the disk image and later restore it, or delete the bootable backup if it is no longer needed.
[B]
Requirements[/B]

This has been tested on Ubuntu 7.04 (Feisty) 32-bit, though it may also work on other versions. Dependencies include os-prober, p7zip-full, and ntfs-3g, though these are automatically resolved when installing the deb package.

**Credits**

This guide and the Bubakup and LVPM applications were created by me, Geza Kovacs. The currently used loopmounting patches are from the Lupin component of the Wubi Project, though Ubuntu 7.10 (Gutsy)'s built-in loopmounting code will be used once it is released.

**Instructions**

If you prefer a graphical, screenshot-based tutorial, see the main site at [http://lubi.sourceforge.net/bubakup.html](http://lubi.sourceforge.net/bubakup.html) otherwise, follow the instructions below:

**Installation**

Download the package file (deb) at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) and install it. You will then be able to run Bubakup by clicking Applications -> System Tools -> Bubakup

**Creating a bootable backup**

Start Bubakup, and select the "Create a backup" option.

A dialog will then prompt you to specify a partition to save the backup to; select a partition and click OK.

The next dialog will tell you how much disk space will be needed by your backup, and if you want to exclude any directories from the backup, select the "Exclude more directories" option and specify the directory. Once you have excluded all the directories you would like to, select "Continue On".

The next dialog will then prompt you how large you would like to make the loopmounted bootable backup disk image, in MB. The minimum value should be enough if you are only using it as a backup/restore/rescue system, but if you aim to install additional software or store additional files on the backup image, for sandboxed testing or other purposes, you may want to give it more space (but remember to not go over the amount of free space on your hard drive). Once you have selected a value, click OK to proceed.

The backup process will then begin, and may take a long time (an hour or more), depending on how much data you backed up and your drive performance.

Once the "Backup Complete" notification appears, you can reboot and select the last option in the menu list, "Bubakup", to boot the bootable backup disk image.

**Restoring a bootable backup to a partition**

If you have a spare partition to restore to, or are willing to overwrite one, you can continue on; otherwise, you will need to shrink an existing partition and create a new one. If you don't have a livecd, you can use the Partition Manager tool at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) to resize your partitions (just install the deb package, boot it, and start GParted), or if you have a live CD, you can use GParted.

Once you have a partition to restore to, boot the bootable backup, and start LVPM at Applications -> System Tools -> LVPM, select "Transfer install to a dedicated partition", select the free partition to restore to, wait as it restores, and you can boot into your newly restored system. A more detailed guide is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

**Archiving a bootable backup**

If you archive a bootable backup and remove the original bootable disk images, you will be unable to directly boot it until you restore the backup. The archiving feature is primarily used for the purpose of saving disk space, and should be used only on older backup disk images that you won't have to boot anytime soon. To archive a bootable backup, start Bubakup (from the primary operating system, not the bootable backup), and select the "Archive existing backup option.

A dialog will then prompt you to select the partition in which the bootable backup disk image you wish to archive is stored in. Select the partition and click "OK".

The next dialog will then allow you to specify which directory you want to save the backup image in. Select a directory and click OK.

The next dialog will then ask how much compression to use, on a scale of 1 to 9. The higher the value, the smaller the file will be, though the time it takes to create the backup will drastically increase.

The archiving process will then begin, and the disk image will be compressed using 7-zip. The process may take over an hour, depending on the size of the original bootable backup disk image and the compression setting you selected. Once it is done, a text dialog will appear.
[B]
Restoring a bootable backup disk image.[/B]

Once you restore a bootable backup disk image from an archive, you will be able to once again boot the loopmounted disk image. To restore, first start Bubakup, and select the "Restore a backup from archive"

A file-selection dialog will then allow you to select the archived backup file (7z extension) to restore from. Select the file and click OK.

The next dialog will then allow you to select the partition to which the archived loopmounted backup disk image should be restored to. Select the partition and click OK.

Then wait as the compressed bootable backup disk image is uncompressed into the selected partition/bbk-$date subdirectory, and the grub menu entries are added to allow for booting from the loopmounted backup disk image.

**Deleting bootable backup images, undoing changes, and uninstalling**

Start Bubakup (from the primary operating system, not the bootable backup), and select the "Delete existing backup" option. 

A dialog will then prompt you to select the partition in which the backup is stored; select the partition and click OK

The next dialog will then list the bootable backups stored on the partition; select the backup you want to delete and click "OK"

The backup will then be deleted, and the GRUB menu entry will be removed.

If you want to remove Bubakup itself, just remove the package "bubakup" using Synaptic.

---

### Post by tuxcantfly on 2007-08-29
I've reposted this thread in the howtos/tutorial section, so see [http://ubuntuforums.org/showthread.php?t=535684](http://ubuntuforums.org/showthread.php?t=535684)

---

### Post by tuxcantfly on 2007-08-29
unsticking thread since it's moved to the tutorials/howtos section

---

