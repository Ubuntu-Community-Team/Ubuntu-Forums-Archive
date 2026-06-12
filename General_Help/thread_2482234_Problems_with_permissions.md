---
title: "Problems with permissions"
date: 2022-12-25
forum: General Help
---

### Post by carlo-sanguineti on 2022-12-25
Hello, I am an Ubuntu user since about 10 years, but I have not a complete knowledge of Linux. I bought a new PC, an assembled one, and I have all the backups of my data from the old PC. I am experiencing problems with, I think, permissions. In my PC there are three disks: a solid state one for the operating system, programs and applications; two hard disks for data and media.
[LIST]
[*]I copied my Thunderbird email local folders in one of the two data HDD. I browsed in settings set the location of local folders. The local folders are correctly shown but their content is invisible and I cannot put an email from inbox to any of the local folders and subfolders;
[*]Document Viewer is able to open a pdf file only if this file is in the solid state disk, I.E. in the Documents folder. If the same file is in one of the two "remote" disks I have this error: [IMG]https://ubuntuforums.org/attachment.php?attachmentid=291449&stc=1[/IMG]
[*]I am able to open ant LibreOffice Files in read-only mode, I can edit them, but not save them overwriting the old one.
[*]All the folders in the Data and Media hard disks are "locked" and I can access to them only opening them as adimistrator.
[/LIST]
There are many other issues like these.
Since I am the only user and administrator of my PC and there is only this account in the PC, how can I get "the ownership" of everything in one (or more) commads / operations, without having those issues and anyway to avoid to open as administrator any folder of my PC and backup disks every day?
Thank you a lot for an answer,
Carlo Sanguineti

---

### Post by Impavidus on 2022-12-25
There are two things that could be the issue here.

First, some applications are stored in snap form these days, as opposed to the original deb form. Snaps are more restricted in what parts of the file system they can access. It's for security, but many consider the extra security not worth the inconvenience. So if the applications you use for those files are snaps, they may be unable to open any files outside your home directory.

Second, there may be something wrong with the permissions used for the additional hard drives. What filesystem do you use on them? How do you mount them? For internal hard drives, it's usually best to mount them automatically at boot time using /etc/fstab.

---

### Post by carlo-sanguineti on 2022-12-25
Thank you for your answer.

I have really no idea if some application are stored in snap, despite I have sometimmes - and I had on the old computer - some warning about snap.

The Operating System disk is formatted parially in FAT (537 MB) and partially EXT4 (1TB); all the other disk, internal or external (the backup ones) are formatted in EXT4. I don't know how to use /etc/fstab; both the internal HDD are not mounted on boot.

At the moment it is quite a nightmare to have the only account, with administrator permissions, and to be forced to open as administrator (I should be the administrator always, I think) some folders, especially when this opening does not affect the subfolders and the files.

Thank you again,

Carlo

Latest News:

I'm really ignorant in Linux! With a change owner (Chown *) command everything want properly.
I'm sorry fot the time was wasted by anyone trying to propose a solution for my issue.

---

