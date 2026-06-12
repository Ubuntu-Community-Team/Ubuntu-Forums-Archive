---
title: "recovering deleted files"
date: 2015-03-20
forum: General Help
---

### Post by mdtycho on 2015-03-20
I accidentally deleted a folder of important video lectures,is there anything I can do to get them back?

---

### Post by pmi2 on 2015-03-20
Yes, but recovery can go from trivial to a major pain in the rear end.  

How did you delete the folder? Did you do if from File Manager, by clicking on "Move to Trash", or on "Delete", or some other way?  Or from inside some application?

In other words, the more information you provide, the easier it will be for others to tell you how to recover the files.

---

### Post by mdtycho on 2015-03-20
I'm using xubuntu,I highlighted the folder,right-clicked and delete.Also emptied the trash.

---

### Post by v3.xx on 2015-03-20
I know of (have not used either) Foremost and Scalpel.  Both are in the software center.

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by pmi2 on 2015-03-20
I have used Photorec, which is part of TestDisk.  It is a very powerful tool, but one has to exercise some caution and discretion in using it, and not run it blindly.  When just run without selecting the file type one wants to recover, it can fill up the whole disk with recovered files and fragments thereof.  If you limit the scope to what you actually want to recover, it does a good job.

If the files were "trashed" and then "Deleted", then more than likely, you will recover other, older versions or fragments created while editing those files.  You then have to find what you need to keep in the folders containing the recovered files, which can take some time.  You also have to rename the recovered files, and then copy them to the original folders.

edit:  I should have added, when recovering files from disk, the target, "recovery" directory should be on a separate partition, disk, or USB drive, never on the same partition as the files that were deleted and are being recovered.

Photorec and the other tools are listed at the link below:

[URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery

[/URL]

---

