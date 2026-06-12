---
title: "As my handle suggests..."
date: 2008-06-09
forum: General Help
---

### Post by computarded on 2008-06-09
Okay, so I'm a little embarrassed. :redface:  I don't know how to do crap, seriously.  I'm a braaaaaaand new linux user and it's proving to be more difficult to learn than I thought it would be.

At any rate, I got a 7z off the net and it's taking f-o-r-e-v-e-r to decompress once I finally figured out how to get it going.  I want to make it stop, but I don't want the leftover corrupted file.  What do I do?

PS Feel free to make fun of me.  I do it all the time. :P

---

### Post by KingTermite on 2008-06-09
Is it a GUI version? Try clicking the "x" in upper right corner of window.

If not, go to a command line and type "ps" and if you see a process for 7zip, note its process number and type "kill <proc num>".

Then you'll have to manually delete the files. Go to directory files were decompressing to ("cd <dir>") and then delete the files with "rm file" for each file.

---

### Post by computarded on 2008-06-09
You are my hero <3

---

### Post by tom66 on 2008-06-09
I find an easier way is to just use "killall <appname>", but it kills all instances of the appname.

---

### Post by VMC on 2008-06-09
I'm using "File Roller 2.22.3" to compress/decompress 7z files, and they are very fast. File Roller will work with RAR, 7z, zip, and a lot more.

---

### Post by computarded on 2008-06-11
I tried file roller and it didn't work, but I think that may have been before I installed 7z.

---

### Post by ad_267 on 2008-06-11
In order for file roller to handle 7z files you need to install either the p7zip or p7zip-full package. Before you install stuff off the internet it's better to search the packages in synaptic package manager. System - Administration - Synaptic Package manager.

---

