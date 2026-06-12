---
title: "Ubuntu hangs when loading filesystem in &quot;Save as..&quot; box"
date: 2008-01-18
forum: General Help
---

### Post by Nexusx6 on 2008-01-18
Hey all,

For some reason that I can't figure out, every time I try to save something in "Save As..." dialog box the app that opened the box will turn grey like its crashing/not responding for a few seconds as it seems to load the filesystem in the "Save as.." dialog box. Oddly enough, it doesn't do this when uploading. Its starting to drive me a little nuts, any help would be really appreciated.

 I've screenshotted FF as its doing this and appended it to the post.

**______SOLUTION______:**
The problem was caused because of a huge amount of load placed on my processor because a massive amount of files and folders were being loaded into the "Places" column. Deleting the parent folder solved the problem for me, but I'm sure that navigating to were the parent folder is, selecting it, and pressing "Remove" under the "Places" menu would do the same thing.

---

### Post by jeffus_il on 2008-01-18
Is this different for different size files, could you do a test with a small file?

---

### Post by Nexusx6 on 2008-01-18
The size of the file doesn't effect the problem; I've tried saving a totally empty, blank, text file and it did the same thing.

---

### Post by jeffus_il on 2008-01-18
Well, bang goes that theory, How about really large folders, many files, maybe 1000'''s??

---

### Post by Nexusx6 on 2008-01-18
I think you're on to something. I've attached another screeny, this time after everything has loaded and the app has recovered. If you look in the left most column you can see a bunch of folders all starting with "DEU". There are **a lot** of those folders, and a bunch more that you can see that all stem from this German Language Pack I was trying to install to practice German. I have no idea how all those folders got loaded into the 'shortcut' area, and though there is a "remove" button, removing them one by one will take me forever ; ;

Anyway to remove them in mass? I can't select more than one at a time via the "Save As..." menu. Also, how did this happen in the first place?

**EDIT:** Bam! It worked! The parent directory that all those folders were under was still in the trash bin. I emptied the trash bin thus clearing all those directories from the "Places" menu and now the problems is solved :D Thanks for your help jeffus! :KS

---

