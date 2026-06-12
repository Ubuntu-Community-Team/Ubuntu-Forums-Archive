---
title: "NTFS (or FAT32) partitions created with GParted in Ubuntu do not show up in Windows"
date: 2007-09-16
forum: General Help
---

### Post by DsurioN on 2007-09-16
I am having problems with an NTFS drive that i created in GParted not showing up in windows.  This is my current partition setup:

Partition 1: EFI
Partition 2: Macintosh HD (HFS+)
Partition 3: Backup (HFS+)
Partition 4: Vista (NTFS)
Partition 5: [Soon to be Windows XP] NTFS (tried FAT32 too, didn't work)
Partition 6: Swap
Partition 7: Ubuntu (ext3)

What I did is I resized the existing NTFS partition (vista), and then created a new one right after it.  This seemed to work fine and the new partition was displaying properly in linux.  Vista still boots.  I want to install windows xp on the new partition (partition 5) but under vista and the xp installer, everything after partition 4 is listed as free space.  I know it won't recognize the linux ones, but is there any way I can format the Windows XP partition to make it visible to Windows?

---

### Post by pxwpxw on 2007-09-16
Windows is only seeing the MBR system partitions, which are probably 1234.
You can run fdisk in either macosx or ubuntu to see the windows view (that holds for xp, probably vista also). and diskutil in macosx will show all partitions, pdisk will show free spaces as well.

macosx can see all, so maybe p3 could be surrendered to xp, and make a new partition for hfs backup. I dont know it that will get xp installed in that configuration, thats another issue.

---

### Post by JBAlaska on 2007-09-16
I believe there's a limit to how many primary partitions you can "see" on a single drive with windoze, and that limit is 4.

I think you should be able to use a extended partition and set logical drives in that beyond 4.

Maybe this bump will get someone who knows more to elaborate.

---

