---
title: "Why must I run fsck manually?"
date: 2022-07-20
forum: General Help
---

### Post by sofasurfer on 2022-07-20
My system would not boot. I did some reading about fsck because I have never used it to repair my system before. I was told to run ***[I]$ fsck -p /dev/sda3*[/I]** so I did. It failed to run and I was told to run the fsck manually by running the same command but without the **-p** option so I did. This involved being asked a bunch of questions about file system terminology to which I just answered "yes" each time.
My question is, why did I need to do, manually, the same thing that could have been done automatically had the original command not failed to run with the **-p** command?

---

### Post by TheFu on 2022-07-20
If the system is telling you to run it, then the system thinks there is something wrong with the file system and it doesn't want to be responsible for more corruption, so it let's you choose what to fix (or not).  It is blame shifting.  The manpage for fsck has options that are worth knowing about, if you don't want to be asked the questions.

Each file system will have a special version of fsck, usually named fsck.{file system name}, so the manpage for each
```
fsck.cramfs  fsck.ext2    fsck.ext4    fsck.minix   fsck.vfat    
fsck.exfat   fsck.ext3    fsck.fat     fsck.msdos   
```
will have specific options that may not be in the main fsck program.  There are other programs too, I just don't have any others installed on the box I pulled the list of fsck* commands from.  Note, there isn't an fsck.ntfs. Use Windows tools for that file system.

And just for clarity, fsck is run against file systems, not partitions.  There can be a 1-to-1 map between the file system and the partition, but that isn't always the situation. Best to be 100% certain that the fsck command is pointing at the file system.

---

### Post by mIk3_08 on 2022-07-21
> **sofasurfer said:**
> My system would not boot. I did some reading  about fsck because I have never used it to repair my system before. I  was told to run ***[I]$ fsck -p /dev/sda3*[/I]** so I did. It failed to run and I was told to run the fsck manually by running the same command but without the **-p**  option so I did. This involved being asked a bunch of questions about  file system terminology to which I just answered "yes" each time.
My question is, why did I need to do, manually, the same thing that  could have been done automatically had the original command not failed  to run with the **-p** command?

It is  recommended to run the fsck when your Linux Ubuntu Operating  System encounters some issues on your storage drive. This is one of the  requirements so that it will clear the issues on your system drive.  It will also required to do it manually maybe due to some issues in your  system storage drive that may causes it to clogged/stock-up and can't process to continue the progress. That is why it should be done step by step or line by line in programing. Regards and cheers.

---

