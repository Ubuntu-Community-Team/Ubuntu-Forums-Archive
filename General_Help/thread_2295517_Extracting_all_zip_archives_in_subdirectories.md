---
title: "Extracting all zip archives in subdirectories"
date: 2015-09-19
forum: General Help
---

### Post by jannis2 on 2015-09-19
I just downloaded some zip archives (names unknown) into some directories. Every zip folder is in a sub-directory of the main directory, never further down in the tree. It can also be more than one archive in a subdirectory. The subdirectories are all in the format YYYY-MM-DD. So we can have the following tree for example:

[FONT=courier new]**main_dir**
  >**2015-09-19**
     >>[COLOR=#ff0000]blabla.zip[/COLOR]
  >**2015-05-18**
     >>[COLOR=#ff0000]blabla.zip[/COLOR]
     >>[COLOR=#ff0000]blabla (1).zip[/COLOR]
  >**2014-07-25**
     >>[COLOR=#ff0000]blabla.zip[/COLOR]
     >>[COLOR=#ff0000]blabla.zip[/COLOR]
     >>[/FONT][COLOR=#ff0000][FONT=courier new]random.jpg[/FONT]

[/COLOR]These directories are now supposed to be extracted in the same subfolder as they are now. In the ideal situation, I also get a file logging what is happening and listing errors etc.

I know of the unzip command, but I didn't get it to do what I want (in a for loop), because some of the zip files contain spaces.

Thanks in advance!
Jannis

---

### Post by steeldriver on 2015-09-19
Hello and welcome to the forums

What command did you try, exactly? Filenames with spaces in them should be simple to handle in shell loops - by proper use of quoting

Or you should be able to use the `find` command with a -exec or -execdir action

---

### Post by jannis2 on 2015-09-19
I used:
[FONT=courier new]for filepath in */*.zip; do unzip $filepath -d ${filepath:0:10}; done[/FONT]

---

### Post by jannis2 on 2015-09-19
But if it could be moddified to log the tasks that would be even better, cause I can only check if everything worked fine by double-checking the archive and sub-directory contents... So getting a list of errors/success messages would be a huge help here

---

