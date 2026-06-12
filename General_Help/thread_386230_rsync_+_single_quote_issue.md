---
title: "rsync + single quote issue"
date: 2007-03-16
forum: General Help
---

### Post by ilvg2k on 2007-03-16
I use rsync to backup files/folders from a windows share mount to a ubuntu box. Some of these files have single quotes in their name (ie: foo's file.txt). 

The issue is when rsync runs, it tries to copy those files with single quotes and it thinks that file has vanished since the shell is trying to use the single quote (') as part of the command rather than part of the file name. 

The exact command I am using is as follows:

      rsync -vrltgo --progress --delete <path_from> <path_to>

I tried to explain this as best I can, thanks for the help!

---

### Post by pt123 on 2007-03-17
what about putting the path in double quotes - "  "

---

