---
title: "Grub problems"
date: 2007-05-18
forum: General Help
---

### Post by rbbrum110 on 2007-05-18
Hi, 
I've got problems when loading windows from grub. i get an error 13 message saying "invalid or unsupported executable format." 
im running a dual operating system with windows 98se on hda and ubuntu edgy eft on a separate hard drive. ive never had problems loading windows ever before with grub. i just recently added some line somewhere so my ubuntu system shuts down properly might that have anything to do with it?

when i type sudo fdisk -l i get the following:
Disk /dev/hda: 15.3 GB, 15364339200 bytes
240 heads, 63 sectors/track, 1984 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1984    14999008+   c  W95 FAT32 (LBA)

Disk /dev/hdd: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2405    19318131   83  Linux
/dev/hdd2            2406        2498      747022+   5  Extended
/dev/hdd5            2406        2498      746991   82  Linux swap / Solaris




and heres what my grub file looks like:
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


any response or help would be appreciated thank you!

---

### Post by Herman on 2007-05-18
Hello rbbrum110,
I don't think any line you could add in Ubuntu anywhere would affect Windows. You might have some kind of problem with your Windows bootsector. Grub chainloads Windows via its boot sector, but for some reason it isn't able to anymore.
Try a file system check from a  [GParted -- LiveCD]("http://gparted.sourceforge.net/") first, (if you have one), because that's the easiest and a file system check is always a good thing to do anyway.

The FIXBOOT command from a Windows  XP [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") would normally be the recommended way to repair a Windows XP bootsector and other files, but I'm not too sure what you do with Windows 98. Can you do that with a Windows 98 boot disc from [Bootdisk.com]("http://www.bootdisk.com/")? Probably you can.

Since it's Windows98 it will have the FAT32 file system, you should be able to fix it from Linux. Run [COLOR=#000000][FONT=Bitstream Vera Sans Mono]dosfsck -ar [/FONT][/COLOR]on it, refer to this link: [                      When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")

Regards, Herman :)

---

### Post by rbbrum110 on 2007-05-18
Thank you for the response, Herman. Unfortunately, none of the methods worked for me. I think there was something wrong with the superboot and when I tried to use a backup they all failed. I ran into a program called e2salvage that im gonna try out

---

