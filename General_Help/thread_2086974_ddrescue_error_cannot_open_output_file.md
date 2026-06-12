---
title: "ddrescue error: cannot open output file"
date: 2012-11-22
forum: General Help
---

### Post by Steve00 on 2012-11-22
I am trying to create an image of a drive before running TestDisk on it. The bad drive is sdc and I have a larger drive as sdb. Both are formatted NTFS.

The bad drive is from a Windows 7 machine and I want to first image the drive and then try running TestDisk to recreate the NTFS Boot Sector (When trying to mount the drive in Windows, we get: "The drive is not formatted, do you want to format it now?".)

When I run:
[sudo ddrescue -r 3 /dev/sdc /dev/sdb/image /dev/sdb/logfile]

I get an error message "Cannot open output file: no such file or directory"

Reading on the forums found a hint that it might be the way I had the logfile command structured. However,

[sudo ddrescue -r 3 /dev/sdc /dev/sdb/image logfile]

resulted in the the same error message.

I'd like to create an image instead of just cloning the drive.

Any suggestions?

Thanks!

--Steve

---

### Post by lechien73 on 2012-11-22
Your ddrescue command is a bit mixed up. If you want to create a hard drive image, then you'll need to mount /dev/sdb first.

If you mounted /dev/sdb to, for example /mnt/sdb, then your command would likely work as:

```
sudo ddrescue -r 3 /dev/sdc /mnt/sdb/image /mnt/sdb/logfile
```

Hope this helps, please let me know if I've misunderstood your requirements.

---

