---
title: "[SOLVED] unmount drive"
date: 2008-01-02
forum: General Help
---

### Post by timboellis on 2008-01-02
I just used sudo bash diskmounter in order to view an external NTFS hard drive.

However now in my PC I have sdg1 and sdh1which it will not let me unmount by either right clicking or sudo umount /dev/sdh1


Also my orginial 500gb Fat32 drive comes up but gives me the error NTFS signature missing any help

This may help 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95e795e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14310072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488391041    c  W95 FAT32 (LBA)

---

### Post by timboellis on 2008-01-02
Sorted I checked the fstab and remove the 2 dead drives and all working now.

Also can anyone tell me how i do fixed and tanks on the forum or do i do this manually

---

### Post by ~LoKe on 2008-01-02
To thank someone, click on the icon under the post that looks like this: [img]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/img].

To mark a thread solved, go to thread tools -> mark as solved.

---

