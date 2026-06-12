---
title: "Problem with terminal?"
date: 2008-01-13
forum: General Help
---

### Post by kreuelt on 2008-01-13
The screenshot pretty much explains it.
[img]http://img183.imageshack.us/img183/4469/screenshotlu1.png[/img]
Yes, I tried sudo.
Any help would be appreciated!

---

### Post by santiagoward2000 on 2008-01-13
Hi!
I'm not quite sure what you're trying to do, but I guess you want to install the compiz-fusion-plugins package. If so, I think you need to untar the file first, and then go to the folder where you did this. To untar it, you can just right-click on it and select **Extract here** or **Extract to...**.
Cheers!

---

### Post by lgambett on 2008-01-13
The problem is the / after the cd command. This instructs linux to start from the root directory, while you are in a subdirectory. Remove the / before the directory name.
A small trick; after the cd command digit the first two or three characters of the subdirectory, then press TAB. Linux will autocomplete the directory name without spelling errors.

---

### Post by Omnios on 2008-01-13
tar and tar.bz2 are comprssed files similar to zip in windows.
 
 There are terminal commands to untar them also 
 man tar 
 tar --help

---

### Post by kreuelt on 2008-01-13
Thanks lgambett! Also, fyi, I already had the directory untarred. I know that much :) I just couldn't figure out what was going on with the cd command. Thanks again!

---

