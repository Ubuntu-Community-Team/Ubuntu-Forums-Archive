---
title: "File Transfer: HFS+ to NTFS"
date: 2013-04-01
forum: General Help
---

### Post by gdea73 on 2013-04-01
This is a rather unfortunate situation and is far from ideal, but I don't have control over the circumstances exactly.

A client gave me a 500GB external hard drive that was supposedly 'broken.' I informed them that there was little I could likely do if the drive itself was bad, but I could disassemble it and try to recover the data from the bare drive. (The warranty had expired long ago.)

I cracked open the case and extracted the Seagate 500GB SATA drive, HFS+ formatted. (Which strangely was labeled as a Maxtor in its external form.) I attached it to a server I'd recently finished because it was the most accessible PC with SATA, and I was able to read from the drive (using a 10.04 server live CD).

Now my dilemma is I've been asked to copy the data from the Seagate 500GB drive to the client's newer Toshiba 1TB drive, which has other data on it and is NTFS formatted.

On the live system, the HFS+ (source) drive is read-only, and the NTFS (destination) drive shows up as octet 777 for most files/directories. I previously tried to simply cp -r everything over, but I ran into an input/output error somewhere along and stopped. Granted this process took 30 hours or more, so I figured it'd be a waste to start over.

This time I used rsync -av to 'synchronize' the partial copy with the source. This seemed to work for several hours again, until it failed at the end with yet another input/output error. In addition it took an incredibly long time, I expected that some of the large files would already be on the destination drive, but it seemed they were being overwritten.

I realized that the input/output error was because the partition of the Toshiba drive (/dev/sdb1) somewhere along was uncounted from /mnt/toshiba and was relabeled as /dev/sdc1. So now I had to manually unmount and remount the drive and restart the rsync job.

My concern is that the Toshiba drive has some sort of auto-off feature, and after a solid 12 hours of disk access, it turns off for a second which causes it to be reassigned a device name. Hopefully the rsync job will finish before this happens again, but I have reason to believe when I get home it will have failed again.

Any suggestions? TIA.

PS: smartctl reported 0 bad sectors on both drives. I also ran a CHKDSK /F on the Toshiba via my XP box before this process.

---

### Post by tgalati4 on 2013-04-01
It could be a bug in the firmware of the Toshiba drive.  If the data is really important, get another drive, format it ext4 and make a decent backup.  Install the ext utilities in Windows so you can read it.  I would be more confident in ext4's file structure than NTFS and it would probably copy faster from hfs+.

---

### Post by gdea73 on 2013-04-02
That would probably be a better workaround, but I just ran the rsync job one more time and it finally worked.
So, copying from HFS+ (journalled) to NTFS is not fun, and the entire transfer went through at ~1.04MB/s, for a large transfer that took a long time.
But it worked, making sure it matches now. I had trouble with part, that was a backup of an entire Mac OS X hard disk, so basically a flattened partition within the partition, but I was able to tarball that and save it to a different backup disk.

Regardless, thanks for your help.

---

