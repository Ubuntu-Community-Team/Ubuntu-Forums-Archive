---
title: "Cannot open windows partitions"
date: 2013-09-05
forum: General Help
---

### Post by hp4 on 2013-09-05
I had installed ubuntu13.04(desktop amd64) in UEFI mode,but I cannot open my windows(windows8 X64) partitions.There's the error information:

Error mounting /dev/sda5 at /media/hp/&#24212;&#29992;&#31243;&#24207;: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda5" "/media/hp/&#24212;&#29992;&#31243;&#24207;"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Help!

---

### Post by prodigy_ on 2013-09-06
Self-explanatory. Make sure you shutdown (not hibernate) Windows and check the NTFS partition with chkdsk.

---

### Post by Mark Phelps on 2013-09-06
When you "shutdown" the Win8 system, it actually goes into hibernation -- and it keeps the drives mounted the entire time.

You have to disable Fast Startup on the Win8 side -- and when you do that, booting into Win8 is going to take a lot longer.

---

