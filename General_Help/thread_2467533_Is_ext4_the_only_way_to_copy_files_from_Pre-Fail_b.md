---
title: "Is ext4 the only way to copy files from Pre-Fail but OK HDD?"
date: 2021-09-29
forum: General Help
---

### Post by tagjaganamuha on 2021-09-29
**OS: **Ubuntu 18.04.6 LTS
**HDD: **ST1000LM024 HN-M101MBB (1,0 TB)
**SMART:** Disk is OK (3 x Pre-Fail, 20 x Old-Age)

I needed to copy 20 MP4 files from old laptop to brand new ADATA 64 GB flash drive. The smallest file was 420 MB and the largest file was 5,8 GB (43 GB in total). 

There are 3 ways of formatting a flash drive (ext4, NTFS, FAT). I tried them all. FAT resulted in "File to large error", NTFS resulted in "Error splicing file: Input/output error" and ext4 was a success.

[B]1. Why only ext4 was a success? 

2. Can I now copy those files from ext4 flash drive to Windows 10 or macOS?[/B]

---

### Post by CharlesA on 2021-09-29
File too large is expected since you have a file that is larger than 4GB when running a FAT file system. You can use exfat instead and it probably would have copied fine.

The NTFS error sounds.. odd since it shouldn't have any problems handling files larger than 4GB.

Did you verify the checksums of the files on the failing disk and the ones on the flash drive?

You can do that with the following command:

```
sha256sum /path/to/file
```

As for accessing Ext4 on Windows 10, it isn't easy since it doesn't support it natively. There are some options for reading ext4 file systems here: [https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10](https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10)

I don't have a mac but all the stuff I found online say that osx doesn't support ext4 without a third party app.

I would verify the hashes of the files and then copy them to another drive that is formatted as exfat or NTFS and see if you run into the same issues.

---

### Post by Impavidus on 2021-09-29
FAT doesn't support files larger than 4GB. Support for NTFS was reverse engineered on Linux. Strange errors may occur, although generally it works. It could be a problem with block allocation, fragmentation, ... I don't know. ext4 is native Linux, so that's most likely to work on Linux.

The classic way to work around issues with large files is to split them into smaller files. You can use the split tool. Read the manual. Merging the parts later can be done on Linux with the cat tool. I don't know what tool you have for that on Windows.

As for that smart status, it looks like there are 3 parameters that, if exceeding a threshold, indicate failure is near and 20 parameters that, if exceeding a threshold, indicate old age. It's just the type of parameter and is always mentioned, even when not exceeding that threshold. Have you actually performed an extensive test before viewing the results? Smart data isn't always easy to interpret.

---

