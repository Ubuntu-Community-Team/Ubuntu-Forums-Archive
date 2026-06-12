---
title: "How to recover a FAT32 partition?"
date: 2007-03-14
forum: General Help
---

### Post by t_huankiat on 2007-03-14
Hi, I had just upgrade from 6.10 to 7.04 yesterday. After I finally done with the installation and configuration needed for my wireless access and the right media codecs, I turned on my two external FAT32 hard disks.

The 320GB loaded with no problem. But the 160GB I have was not showing at all. I rebooted to Windows just to make sure. The 160GB was detected and I could see all the folders. The weird thing is the video files I have no longer playable (The media player simply says opening without actually playing anything).

So I rebooted to Ubuntu again. Still no sign of the 160GB. So I opened GParted which I installed since 6.06. I found the drive, but it no longer belong to any file system format. The night before I did the upgrade, I was still able to play videos from the drive just fine.

Call me stupid, or maybe it's too late at night, I actually selected the option to format the drive to FAT32 without any hesitation! I think I was under the impression that after re-format the drive, all the files and folders would miraculously reappear since that's what happened to the same drive few months ago when I converted it from NTFS to FAT32 (for the switch to Ubuntu).

So now I have a hard drive that appears to be empty in Windows, and not mounted at all in Ubuntu (but shown in GParted). I haven't done any writing to the disk, so I am assuming that the data should still be in there.

How can I restore the data or even the FAT? I searched the forum, seems like TestDisk is an option. I am tempted to proceed right away, but after this incident, I guess I can wait for a few more hours and seek some advices from the experts before I do anything stupid again.

*I still can't understand what had happened. The upgrade to 7.04?

---

