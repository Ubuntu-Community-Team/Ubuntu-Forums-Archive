---
title: "Can't Mount NTFS partition, other partition on same physical drive works fine."
date: 2015-11-12
forum: General Help
---

### Post by Hishighness on 2015-11-12
Good day all, I've got an external SATA hard drive and it's got 2 partitions on it, both are NTFS. One of the partitions I can access with no problem so I know the hard drive is readable but the other gives me an error whenever I try to mount it.

[FONT=arial]Error mounting /dev/sdf6 at /media/hishighness/600gb: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdf6" "/media/hishighness/600gb"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error[/FONT]
[FONT=arial]Failed to read NTFS $Bitmap: Input/output error[/FONT]
[FONT=arial]NTFS is either inconsistent, or there is a hardware fault, or it's a[/FONT]
[FONT=arial]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows[/FONT]
[FONT=arial]then reboot into Windows twice. The usage of the /f parameter is very[/FONT]
[FONT=arial]important! If the device is a SoftRAID/FakeRAID then first activate[/FONT]
[FONT=arial]it and mount a different device under the /dev/mapper/ directory, (e.g.[/FONT]
[FONT=arial]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation[/FONT]
[FONT=arial]for more details.[/FONT]

I was going to try chkdsk but I've got another problem, I just installed Ubuntu yesterday (To try to help with this issue) and when I try to access windows from grub it just sits there with a blank linux screen (I can tell from the color) and won't go in to windows 8.

I honestly don't care about getting in to windows 8 I was just going to switch anyway, what I'm most concerned with is getting the data from the aforementioned drive.

Any help would be appreciated. :)

---

### Post by leunam12 on 2015-11-12
Try boot-repair to fix you Windows booting issue and then try chkdsk.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

