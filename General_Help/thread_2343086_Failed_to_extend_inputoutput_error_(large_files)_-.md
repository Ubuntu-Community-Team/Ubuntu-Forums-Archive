---
title: "Failed to extend: input/output error (large files) - 14.04"
date: 2016-11-13
forum: General Help
---

### Post by nmw01223 on 2016-11-13
I am trying to copy some large files on a 14.04 system to a USB drive. The source partition is ext4, the destination is NTFS (formatted on a Windows system, lots of spare space  - around 160GB, no errors).

The files are system backups and consist of 1 or more files of 4.7GB size, following by a 'tail file' smaller than that - typically 2-2.5GB.

Cannot copy the big files, can copy the smaller ones. I tries this first with the GUI (Thunar), then using cp. The cp errors are:

cp: error reading &#8216;/media/nick/Backups/161112A_full_b1_s1_v1.tib&#8217;: Input/output error
cp: failed to extend &#8216;/media/nick/TOSHIBA EXT 500GB/backups/Nick-4/161112A_full_b1_s1_v1.tib&#8217;: Input/output error

Thought it might be something to do with the USB NTFS drive, so changed the destination to /home/nick. Exactly the same error. Tried it after sudo'ing. No difference. Tried Nautilus, no difference (error given by Nautilus 'error splicing [source] file: input/output error).

The destination file is always 268MB long after the failure.

Seems like there may be a problem copying files bigger than somewhere between 2.5G and 4.7GB, even though both files systems support large files, or maybe for some reason the source is faulty (though it verified OK). Seems unlikely but is this right? Is there a way round it?

---

### Post by sudodus on 2016-11-13
I have copied files much larger than that between ext4 and NTFS, so I think there is special problem here.

1. Maybe the file names make the tools think these files are chunks of a huge file, that should be concatenated to one single file, but something is missing, so it does not work. (I don't think this is the case, but I am not sure.)

2. The file &#8216;/media/nick/Backups/161112A_full_b1_s1_v1.tib&#8217; is bad. For example, it might be written to a part of the drive, where there are bad sectors, that cannot be read from, or the file system is damaged.

3.The location on the target drive (the TOSHIBA EXT 500GB), where it is trying to write, contains bad sectors, that cannot be written to, or the file system is damaged.

4. Some software might have problems because there are spaces in the label (and hence the mountpoint) of the used partition on the target drive. You can unmount (not eject) the USB drive and change the label with ***gparted*** to for example 'Toshiba_ext_500', unplug and re-plug the USB drive and try again.

-o-

2 and 3: You can check and if necessary repair the file systems (and if necessary mark bad sectors to be avoided); use Windows for NTFS and the linux tool e2fsck for ext4. See this link (it is valid not only for pendrives but also for SSDs and HDDs),

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

