---
title: "How to move tons of file that in tons of folder"
date: 2014-02-01
forum: General Help
---

### Post by rucitaf on 2014-02-01
I just recovered jpg and png files from my broken hardisk using  photorec, the result all files was recovered and stored in folder name  recup_dir.1. But the problem is the folder begin from recup_dir.1 to  recup_dir.9999 by name. Means that the number of folder is a lot and  each folder contain 500 files. I want to sort it out because some of jpg  files is just tumbnails or web small pictures that has been recovered  from internet history. How could I sort the file based on size and move  it securely to certain folder, so I can get ride of the rest.

---

### Post by tgalati4 on 2014-02-01
While viewing the directory of files in Nautilus, View==>List (or Control-2) and hit the "Size" column.  That will sort the list by size.  Then use the mouse to select the group of files based on your size criteria.

Otherwise you would need to use the *find* command to do it in a terminal as part of a script to automate what you want to do.

```
man find
```

Some extensive examples:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  Apparently, this has happened before to folks.

---

### Post by SeijiSensei on 2014-02-01
How complicated do you wish to make this?

Most cameras I've used name their image files with upper-case ".JPG" as the extension.  If that's true for you, then you can move all these files to another directory by going to the directory above the recovery ones and using the command:

```
mv -f */*.JPG /path/to/new/folder
```

The "*/*.JPG" item matches all files ending in .JPG in all directories below the current one.

Other solutions would require a script to iterate over the recup_dir.* directories. use the find command to select only those files greater than a size criterion, and move them to the destination folder.

---

### Post by oldfred on 2014-02-01
Photorec has scripts to sort. And you can rename music & photos from internal data. Other are a manual process.

 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by rucitaf on 2014-02-02
Thank you every body... I have learn much from this....

---

