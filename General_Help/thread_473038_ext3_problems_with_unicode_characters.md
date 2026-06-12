---
title: "ext3 problems with unicode characters"
date: 2007-06-13
forum: General Help
---

### Post by wojtekz on 2007-06-13
Hi,

I ran into a problem when I switched from my PowerPC based mac mini to a new Intel based mac. The problem is that I cannot access any files or directories that contain special characters (e.g. German "umlauts") after attaching my ext3 formatted external hard drive to the new machine. All files and directories that contain no special characters are fine and can be accessed without any problems.

Here are some details for the original setup:

Former machine is a PPC mac mini running Ubuntu 7.04 (orignally Ubuntu 6.x, upgraded repeatedly). The new machine is a Intel based mac mini running Ubuntu 7.04 too. Problem is that I don't have my old machine anymore and I need to access my files. Here's how the files appear on the new machine:

drwxrwxr-x   2 1000 1002  4096 2006-09-03 06:27 RegularDirectoryName
?---------   ? ?    ?        ?                ? DirectoryNameWithSpecialCharacter

Strange thing is that all files are accessible when I boot the machine with an old knoppix cd (2.4 kernel). Any new knoppix cd (2.6 kernel) or other ubuntu versions have problems with all special character files. An ls on those files doesn't even show any inode entry.

Any idea are greatly appreciated!

Thanks in advance,
Wojtek

---

