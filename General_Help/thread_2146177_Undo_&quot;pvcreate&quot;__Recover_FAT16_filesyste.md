---
title: "Undo &quot;pvcreate&quot; / Recover FAT16 filesystem?"
date: 2013-05-17
forum: General Help
---

### Post by alex-s77 on 2013-05-17
Hi

I wanted to add some space to my LVM Volume Group and so I created a new partition and wanted to run

[FONT=courier new]pvcreate /dev/sda11
[/FONT]
Well… An alien came by and hit the <enter> key, before I could type the 2nd "1" and thus I entered

[FONT=courier new]pvcreate /dev/sda1[/FONT]

Or something like that :)

On /dev/sda1, I used to have a FAT16 "DELLUTILITY" partiton with partition type "de".

Is there a way to recover from this, gotta repeat, "alien induced mistake"? :)

Thanks a lot,
Alexander

---

