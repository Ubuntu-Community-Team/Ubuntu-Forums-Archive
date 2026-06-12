---
title: "Batch convert .cbr to .cbz"
date: 2021-06-29
forum: General Help
---

### Post by Juanchi-09 on 2021-06-29
Hello there! I found this thread, but I can't really get it to work 'cuz the links are dead: [https://ubuntuforums.org/showthread.php?t=1273762](https://ubuntuforums.org/showthread.php?t=1273762)
I need to convert .cbr files to .cbz because my tablet software can't read .cbr, thank you for any help.
I also found this ([https://github.com/oogg06/cbr2cbz](https://github.com/oogg06/cbr2cbz)) but I don't want to rename all my files.

---

### Post by Holger_Gehrke on 2021-06-29
Post #5 in the thread you link to contains the complete script. I don't see the problem. Copy and paste into your favorite editor, save as 'cbr2cbz' in either ~/.local/bin or ~/bin so the script is in the path and make it executable ('chmod u+x ~/bin/cbr2cbz' in a shell).

Alternatively you could use a viewer that supports cbr; I use Perfect Viewer in the free version on Android and it does the job.

Holger

---

### Post by Juanchi-09 on 2021-06-29
I can't use any other viewer, the tablet is so old I had to resort to old apk versions and stuff. I have no idea what I'd done wrong with the script, but now it works like a charm. Thank you!

---

### Post by ActionParsnip on 2021-06-30
Please remember to flag the post as solved

---

### Post by Juanchi-09 on 2021-07-03
Ah, I was about to, but then I had another question, if I may. Is it possible to apply this recursively to all subfolders and to delete the .cbr files after conversion? Thank you.

---

### Post by The Cog on 2021-07-03
Try this. cd to the top-level folder containing the cbr files, then:
```
find -type f -name '*cbr' -exec cbr2cbz '{}' \;
```

---

### Post by Juanchi-09 on 2021-09-07
> **The Cog said:**
> Try this. cd to the top-level folder containing the cbr files, then:
```
find -type f -name '*cbr' -exec cbr2cbz '{}' \;
```
Thank you. Any difference with for a in *.cbr;do cbr2cbz "$a";done?
Anyways, this is solved!

---

### Post by erind on 2021-09-07
> **Juanchi-09 said:**
> Thank you. **Any difference with for a in *.cbr;do cbr2cbz "$a";done?**
Anyways, this is solved!

As it is a for loop will work only in the current directory, whereas find will descend recursively down the directory tree. 'Find' is a very powerful tool.

---

### Post by Juanchi-09 on 2022-07-25
> **Holger_Gehrke said:**
> Post #5 in the thread you link to contains the complete script. I don't see the problem. Copy and paste into your favorite editor, save as 'cbr2cbz' in either ~/.local/bin or ~/bin so the script is in the path and make it executable ('chmod u+x ~/bin/cbr2cbz' in a shell).

Alternatively you could use a viewer that supports cbr; I use Perfect Viewer in the free version on Android and it does the job.

Holger

I would like to add, for anyone who might find themselves on the same  footing, that, at least in Linux Mint, the directories to which one has  to add the "cbr2cbz" file are "/usr/bin" or "/usr/.local/bin" (with  elevated permissions).

NOTE: If you've got .zip files, just do "rename "s/zip$/cbz/" *.zip" to rename them to .cbz.

So, basically, you create the text file, name it "cbr2cbz", and paste this:
```

#bin/bash

cbr=$1
start_directory=`pwd`

cbz=`basename "$cbr" .cbr`.cbz

tempdir=`mktemp -d`
cd "$tempdir"
unrar e -inul "$start_directory/$cbr"
zip -q "$start_directory/$cbz" *
rm -rf "$tempdir"

```

Then you simply do "sudo mv cbr2cbz /usr/local/bin" from a terminal placed in the directory you've got the "cbr2cbz" file (so that you add it to PATH), and you've got it! Now just go to the directory where the .cbr files are and use either:

Without deleting .cbr files: ```
for a in *.cbr;do cbr2cbz "$a";done
``` 
Does not delete the original file and only works on the directory you're in.
NOTE: If you also want to delete the .cbr files after conversion, just  use "sudo rm -rf -d ./*.cbr" which deletes all files with .cbr extension  in the current directory.

Deleting original .cbr files after conversion (in one directory):
```
for a in *.cbr;do cbr2cbz "$a";done && sudo rm -rf -d ./*.cbr
```


```
find -type f -name '*cbr' -exec cbr2cbz '{}' \;
```
Also does not delete the original file but works across all subdirectories, but the files are placed all on the directory you're in.
NOTE: If you also want to delete .cbr files after conversion from ALL directories and subdirectories (starting from where you are), just do "find . -type f -iname \*.cbr -delete".

Also deletes original .cbr files after conversions (in directory you're in and all subdirectories; files are placed all in the same directory):
```
find -type f -name '*cbr' -exec cbr2cbz '{}' \; && find . -type f -iname \*.cbr -delete
```

USE THE DELETE FUNCTIONS WITH CAUTION, since they might also delete .cbr files that are actually .cbz (so they don't get converted) and actually just need to be renamed.

---

