---
title: "Rsync Hidden Files"
date: 2017-05-27
forum: General Help
---

### Post by juancompadre on 2017-05-27
Hi, I want to use rsync to create backups of my home directory. I do not want to include the hidden files or folders in "/home/user/" so I use --exclude=".*/"  and --exclude=".*" However, I have some hidden files inside some folders that I would like to include. How can I include the hidden files and folders inside any folder like "/home/user/folder/"? Thank you.

---

### Post by Keith_Helms on 2017-05-27
I'm just guessing here, but I'd try changing your exclude rules to
```
--exclude="/.*/"  and --exclude="/.*"
```
If I'm reading the rsync doc correctly, putting a leading slash on the rule will "anchor" it to the top of the path you're syncing from.

---

### Post by SeijiSensei on 2017-05-27
If you only want to exclude hidden files in /home/user, then just write a specific exclusion for those:
```
--exclude=/home/user/\.?*
```

If you have lots of exclusions or inclusions, it's often easier to put them in a file and use the "--exclude-from=/path/to/exclusions/file" instead.

---

### Post by Dennis N on 2017-05-27
I would do two rsync runs:

1st run: exclude all hidden files;
2nd run: use the **--files-from=** option to sync selected hidden files.

---

