---
title: "Non-ASCII filenames rendered incorrectly"
date: 2006-09-16
forum: General Help
---

### Post by Fibonacci on 2006-09-16
Hello,

I'm using Ubuntu LiveCD and am having some problems with non-ASCII characters (e.g. accented characters, ñ, ç, etc) on filenames on my hard disks. Namely, they are rendered incorrectly (or not rendered at all - they appear as a question mark) on the FAT32 disk, but appear fine on the ext3 disk.
Strangely enough, the situation is reversed with Knoppix - no problem on FAT32, strange rendering on ext3. Neither Fedora Core, which is installed on the ext3 disk, or Red Hat, when accessing my computer remotely through SSH, have any problem with either. Windoze renders those on the FAT32 disk correctly (of course, it won't even read the ext3 disk - I know about the drivers but don't want to install them).

How can I fix this?

Thanks in advance,

-Fibo

---

### Post by Fibonacci on 2006-09-17
No way I'm installing Ubuntu if I can't even read the names of the files on the FAT32 disk - it's even worse than what happens with Knoppix.

---

### Post by mssever on 2006-09-17
Try adding the utf8 option to the partition's entry in /etc/fstab and remounting. For example:
```
/dev/hda1       /media/hda1          vfat    defaults,[COLOR=Red]**utf8**[/COLOR],umask=007,gid=46 0       1
```


[FONT=Trebuchet MS][SIZE=1][COLOR=Gray]My 500th post![/COLOR][/SIZE][/FONT]

---

### Post by Fibonacci on 2006-09-21
Thank you, it worked ^^

---

