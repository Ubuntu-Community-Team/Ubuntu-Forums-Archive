---
title: "Problem with folder name extra space which give error on windows"
date: 2013-11-29
forum: General Help
---

### Post by abdorefky on 2013-11-29
i created all my folders on  ext4 partition . i moved the data to NTFS partition and forrmated the ext4 

now most of my files inside the folder dont open and dont move and dont do any thing !!!


what is this !!

 [ATTACH=CONFIG]248199[/ATTACH][ATTACH=CONFIG]248200[/ATTACH]

---

### Post by abdorefky on 2013-11-29
looks like there are a "space character added to the name ! "

---

### Post by abdorefky on 2013-11-29
it even goes with ubuntu to miss up with my windows folders ????

[ATTACH=CONFIG]248201[/ATTACH]

---

### Post by Mark Phelps on 2013-11-29
Did you check the content of the folders and files in the NTFS partition BEFORE you reformatted the Ext4 partition?

If you did, there's no reason why now, you can no longer open files or folders in the NTFS partition.

If the files and folders were already corrupted when you "moved" them, there is no way to salvage them now in the NTFS partition.

However, you may be able to use Testdisk to recover files from the Ext4 partition. See link: [http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery]("http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery")

---

### Post by abdorefky on 2013-11-29
i have justed tested some of the files that i discovered the errors on it from the ubuntu . 
the files are working . and after deleteing the extra space from the folders name it went back to work on windows . 

but its anoying to switch to ubuntu every time i discover an defective folder name !

---

### Post by abdorefky on 2013-11-29
thanks for your help

---

