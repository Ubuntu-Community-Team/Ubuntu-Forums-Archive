---
title: "Copying mass files without file names"
date: 2022-04-20
forum: General Help
---

### Post by MibunoOokami on 2022-04-20
The story: I was given a challenge of recovering data from a poked HDD that had been overwritten several times. Not much of a challenge, Photorec took care of that. 


The problem: just under 600GB of data was recovered and has been spread through 2100+ directories. The HDD belongs to an elderly person, and I can’t expect them to go through each directory finding what they want (primarily photographs). I’ve gone through the first 50 directories, and found it to be too time consuming.


The requested solution: If I place all 2100+ directories into a single one, is there  a cp or rsync command that I can use to copy all .jpg, .png, .pdf etc from the single directory into a new one dedicated to those filetypes? 


It would be great to get all files into their respective directories in a timely fashion. Thank you in advance for any solutions/advice.

---

### Post by btindie on 2022-04-20
You can just use the find command to find files based on the extension.
e.g. the below will copy all .jpg + .png files into the /absolute/path directory preserving timestamps, set that to the correct location of where you want them saved. Change 'recovery' to the directory containing all sub-directories you want to search.
```

find recovery -type f \( -name \*.jpg -o -name \*.png \) -execdir cp -p -t /absolute/path '{}' +

```
You can see how many files would be copied using
```

find recovery -type f \( -name \*.jpg -o -name \*.png \) -print | wc -l

```

---

### Post by oldfred on 2022-04-20
If Photos you can use the internal tags to rename photos.

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by HermanAB on 2022-04-20
Careful!!! Files with identical names will be overwritten.

---

