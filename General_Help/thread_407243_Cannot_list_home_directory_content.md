---
title: "Cannot list home directory content"
date: 2007-04-11
forum: General Help
---

### Post by Chryana on 2007-04-11
Hello. I would like to thank all those who replied to my earlier problem, which had to do with my kubuntu edgy box setting the wrong dns after a while. It seems to be working fine for now. Anyways, I have a new problem. After booting into windows and transferring a few files from two different directories in linux partitions to ntfs ones, I am now unable to list the content of the directories on those partitions under linux. I don't think it's a problem with the hard drive, as I have other partitions which are still working fine on that drive under linux. The two partitions are of type ext3. One of the partition was accessed with Ext2 IFS, and the other with Explore2fs. The partition accessed with explore2fs is my home directory, so the problem is quite annoying. What is strange is that I made no change whatsoever to my home directory, I only copied one file from it. I cut a directory with maybe a dozen files into it from the second partition and pasted it into an ntfs partition. Both partitions can still be seen without problems while I am under windows. However, if I boot linux, the command ls hangs, and it stays in the process table even if do sudo kill on it. Konqueror doesn't show anything either. Also, the two partitions cannot be dismounted: I get the error message "device is busy". I tried booting linux into recovery mode, and then I can dismount the two partitions fine, but I still cannot list their content. I got the error message "Segmentation fault" once or twice while using ls, but most of the time, the ls command just hangs with no reply. One last thing. I can still cd into directories under my home partition, and list their content. The same cannot be said about the second partition I am having trouble with. I tried doing fsck while under recovery mode, and the command came back with no problems found. Feel free to ask me questions if you need more information. As a last resort, I guess I could boot into windows, copy everything and reformat the partitions, but this would take some time, as I would have over 30 GiB of content to copy over. This is all the information about the problem I can think of. Any help or suggestion would be appreciated. Thank you very much.

---

### Post by Chryana on 2007-04-13
The problem fixed itself mysteriously. :confused:  I have no idea why. Well, I guess it's better than having to move gigs and gigs of data around.

---

