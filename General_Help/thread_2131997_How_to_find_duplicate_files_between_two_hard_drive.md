---
title: "How to find duplicate files between two hard drives?"
date: 2013-04-03
forum: General Help
---

### Post by aerohix on 2013-04-03
Hello all!
So, I ruined my hard drive last week and recovered all my stuff with photorec (1 TB) but I still lost my folder structure and file names.
The thing is that I had a whole back up from 2 months ago in another hard drive, all I want to do is to recover my new files and files I've edited, but I can't find a way to compare'em both and delete the duplicates found by photorec.
Can anyone help me? Thanks!

---

### Post by Kirboosy on 2013-04-03
Welcome to the Ubuntu Forums!

Try fslint (File System Lint)

```
sudo apt-get install fslint
```

The reason I recommend this tool is because it has a GUI and is pretty straight forward. This should get you pointed in the right direction. Let me know if that doesn't work for you.

~Caboose

---

### Post by oldfred on 2013-04-03
Part of the issue I had with Photorec was not only did it recover my files, but it recovered every copy. Some were my text files from notes on this site which I update daily with new info and backup was several weeks old. So I had multiple copies of text files all with some changes. 

 Use scripts to help sort and rename files also suggest fslint:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Zill on 2013-04-03
aerohix:  You might like to take a look at [Meld]("http://meldmerge.org/") - it's in the repos.

---

### Post by Greco2002 on 2013-06-19
> **aerohix said:**
> Hello all!
So, I ruined my hard drive last week and recovered all my stuff with photorec (1 TB) but I still lost my folder structure and file names.
The thing is that I had a whole back up from 2 months ago in another hard drive, all I want to do is to recover my new files and files I've edited, but I can't [find duplicate files]("http://www.ashisoft.com") a way to compare'em both and delete the duplicates found by photorec.
Can anyone help me? Thanks!

I too lost my new hard drive its just 3 months old... I don't know what quality product they are making nowadays.

---

