---
title: "[SOLVED] unable to boot after crash, harddisk not mounting"
date: 2008-02-05
forum: General Help
---

### Post by foggydude on 2008-02-05
*EDIT: solved it: it was fsck and i had to figure out right comando's

hello,

- This post is about a GRUB 17 error, but different then all i have found so far. I am new to linux. Is the answer in fsck, and if yes: howto? - 

1. I work on my mythbuntu 7.10 from my windows pc on a local network. After putting it on "pauze" last night, this morning the pc was unresponsive. I rebooted, but got the following error:

*grub error 17*

Most questions regarding this are related to dual booting. that is not my case: i only have ubuntu/mythbuntu

2. i can boot from the live cd. But from the harddisk (4 partitions), only the swap partition gets mounted (/dev/sda3). Other partitions sda1, sda2 & sda4 are in gparted marked with an warning sign. viewing the properties gives :
*****
warning:
unable to detect filesystem! possible reasns are:
-the filesystem is damaged
-the filesystem is unknown to Gparted
-there is no filesystem available (unformatted)
*****

this problem has been posted on the forums. But mostly, it has to do with NTFS formatting. that is not my case: 2 of them are ext3, one is xfs or jfs. they were formatted and worked, so probably damaged.


3. the solution i may have found is "fsck". However, i cannot operate it.  This might because i dont fully understand the manual pages. This might also be because the partitions are not listed in /etc/fstab. the file reads the following:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defeaults 0 0
```

My questions are the following:
[LIST=1]
[*]Am I looking in the right direction with fsck?
[*]Do i need to do anything in etc/fstab, if yes: what?
[*]what exactly should i type to make fsck do its magic?
[*]Is there any hope for my thesis???
[/LIST]

thanks a lot in advance... I threw out windows as it made me crazy, but now my thesis seems completely lost....

---

