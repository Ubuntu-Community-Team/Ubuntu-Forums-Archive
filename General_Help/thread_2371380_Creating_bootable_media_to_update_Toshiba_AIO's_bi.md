---
title: "Creating bootable media to update Toshiba AIO's bios"
date: 2017-09-14
forum: General Help
---

### Post by DAB4970 on 2017-09-14
Hello everyone.  I've recently replaced the mobo on a Toshiba LX835-D3203.  It's bios version is 1.0 something.  I would like to update it to version 6.20, creating the bootable media with the correct file(s) using Ubuntu 16.04/3.  I've searched the web for information on how to do this correctly.  Creating a bootable thumb drive or cd has been troublesome, and knowing how many of the files from within the archive file, downloaded from Toshiba support, needs to be put on the bootable media.  I've tried using "startup disk creator", "disks" and "brasero" to place all the files onto a bootable thumb drive or cd, to no avail because each of those will only allow only 1 file onto the media.  Maybe there's just a stupid-user error in the process.  As far as using anything through the terminal, I don't want to mess anything up by putting an option that doesn't need to be there or not putting in an option that needs to be there.  I'd like to find step by step instructions for dummies, to make sure I'm doing things correctly.

Finding someone with a Windows pc that would allow me to use it for this task is scarce.

---

### Post by oldfred on 2017-09-14
The apps you mention are primarily for creating bootable Linux flash drives from an ISO. And Ubuntu ISO are now hybrid or both DVD & USB flash drive, so they can use dd to image copy ISO to flash drive.

I do not have a newer Toshiba, but my motherboards have several ways to update.
Directly from UEFI (I think older BIOS also) from any FAT32 partition. I believe I once updated just by copying update files into my ESP - efi system partition on hard drive.
From a FAT32 formatted flash drive with boot flag. Just copy files to flash drive and from UEFI read flash drive.
From a DOS bootable flash drive (FAT32) with DOS bootable files and update files. I have seen vendors offer the full download of open source DOS to install to flash drive.
Directly from Windows. (never have used that).

I believe FAT32 is always required for any format as that is the only format UEFI has a driver for.
Also have seen where Linux is developing UEFI update directly from Linux. But I think UEFI has to be a newer version.

---

### Post by DAB4970 on 2017-09-14
So where can I get the DOS bootable files?  I've heard of FreeDOS.  Would that be it?

Apparently, syslinux is a collection of bootable files, DOS, FAT and NTFS.  Why wouldn't there be any application/program with GUI to complete this task?

Update:  Bios updated successfully.  Here's what I did:  from the downloaded file from Toshiba support, I extracted all the files from within the .exe file.  I went to the directory where those files were extracted to and left-clicked on the .iso file and the application that showed itself in a small window was "Image Burning Setup".  I burned that file to a blank cd-rom and rebooted into that cd.  The Bios was successfully updated from that.

I was almost ready to kick the bucket on this task.

---

