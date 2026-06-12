---
title: "What is GNU/Linux's equivalent of Windows' &quot;clean&quot; command?"
date: 2016-01-01
forum: General Help
---

### Post by KayeNg on 2016-01-01
[URL="http://www.sevenforums.com/tutorials/52129-disk-clean-clean-all-diskpart-command.html"]
http://www.sevenforums.com/tutorials/52129-disk-clean-clean-all-diskpart-command.html[/URL]

Can the "clean" command wipe everything including the head of the disk, the mbr?

If I use gparted in a Lubuntu live USB to complete wipe everything, will that suffice? Same effect as windows' "clean" command?

I'm asking because I can't seem to boot a newly installed windows 7 but I can boot the lubuntu os. (It's supposed to be a dual boot system).  I'm thinking the mbr may be corrupted?
 
I'm also thinking of taking out the ram for a few minutes and put it back in and run the computer. see if it works. probably won't.

Thanks

---

### Post by Sweet_Baby_Jamie on 2016-01-01
The easiest way is to re-install Lubuntu and choose the option that wipes away everything but a fresh installation!  Back up everything you want to keep first, of course.

---

### Post by sudodus on 2016-01-01
If you want a dual boot system, and are ready to install both Windows and Lubuntu, and want to do it the easy way, I suggest that you

1. Set the computer into BIOS mode (not UEFI mode)

2. Install Windows

3. Boot into Windows and inside Windows shrink the Windows partition to create space for Lubuntu.

4. Reboot into Windows and check that it recognizes the modified partition and file system (after shrinking). Make sure that you have shut down Windows completely. It must ***not*** be hibernated or semi-hibernated - then Lubuntu's grub might not recognize it or boot into it. (Shutting down is usually easier to do correctly with Window7 than with newer versions of Windows.)

5. Boot into a live session of Lubuntu

6. Start gparted and createhdparm

- an extended partition of the unallocated space
- an ext4 partition (to become the root partition of Lubuntu)
- a swap partition - the size depends on if you plan to use hibernation

7. Start the Lubuntu installer and select ***Something else*** at the partitioning window.

- select the ext4 partition (to become the root partition)
- check that the bootloader will be installed into the head of the correct drive (often but not always /dev/sda, the head of the first internal drive, letter a)

8. I think you know already the following steps in the installer.

After reboot you should have a working dual boot system.

***Edit 1:***

There is more work to do:

- Updating Windows7 to be up to date will take a long time, and you need a separate virus program.

- Check how the graphics and wifi works in Lubuntu, and if necessary install proprietary drivers. Updating Lubuntu to be up to date will also take some time, but is usually faster than for Windows.

- If there are some peripheral devices, you may need drivers both for Windows and Lubuntu.

***Edit 2:***

If you want to clean the internal drive in order to

- make the installation work correctly, it is enough to [wipe the first megabyte](https://help.ubuntu.com/community/mkusb/wipe).

- remove all traces of previous data for privacy, you should use ***DBAN*** or ***hdparm***.

---

### Post by yoshii on 2016-01-01
I don't think the MBR is corrupted.  I think if it was, Linux wouldn't boot either.  I'm guessing that it's one of the Windows boot files that is missing or corrupted of maybe you need to set the boot flag to on for your Windows partition (using gParted).

---

