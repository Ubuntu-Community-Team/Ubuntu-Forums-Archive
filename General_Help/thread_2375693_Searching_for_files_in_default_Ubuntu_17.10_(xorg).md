---
title: "Searching for files in default Ubuntu 17.10 (xorg)"
date: 2017-10-26
forum: General Help
---

### Post by mfox on 2017-10-26
I can't seem to figure out how to search for files from Activities in Ubuntu 17.10 gnome (xorg). When I hit the key that opens the search option, I can type a search term in it, but it doesn't find any files with that term, even though I know they're there. Ubuntu Unity used to do that without problem; doesn't this work in Gnome? Note that I am using the Ubuntu default desktop. The files that I am typically looking for are ones that were recently opened, but even the two "recent" extensions for Gnome shell don't work when installed in the default desktop. A solution involving either "find" or access to recent files would be very helpful.

---

### Post by TheFu on 2017-10-26
**locate** is how I find files that were on the system overnight.
**find** is how I find files that are new today.

Locate is easy to use. ** locate {part of file name}**

The locate DB update process won't search portable storage devices by default.'

If you want full text search, then **recoll** is the best tool I know.

---

### Post by monkeybrain20122 on 2017-10-27
> **mfox said:**
> I can't seem to figure out how to search for files from Activities in Ubuntu 17.10 gnome (xorg). When I hit the key that opens the search option, I can type a search term in it, but it doesn't find any files with that term, even though I know they're there. Ubuntu Unity used to do that without problem; doesn't this work in Gnome? Note that I am using the Ubuntu default desktop. The files that I am typically looking for are ones that were recently opened, but even the two "recent" extensions for Gnome shell don't work when installed in the default desktop. A solution involving either "find" or access to recent files would be very helpful.

gnome shell doesn't have a function to search files in the dash. You have to use the file manager (of course the command line with locate always works but I don't think that is what you want) There was an extension using tracker but it is broken and has not been updated for three years. You would have to install some third party program if you don't want to use the file manager. This is one of the reasons why I still use unity (sudo apt install unity-session xserver-xorg-input-synaptics, then login to unity)

---

### Post by vanadium on 2017-10-27
Actually, I believe tracker is not installed by default on Ubuntu 17.10, which is why there is no file search functionality in Gnome Shell. However, do not hold your breath. File search in Gnome Shell is quite inadequate. For one, apparently you cannot search files without having also the file content indexed. File indexing results in high CPU use, for a long time the first time it is run, but also for many minutes each subsequent session. Then, gnome shell finds what it wants. I had a file in Libreoffice format and another with the same name in doc format: Shell would only find the word version. Next, Shell only shows 10 results. If you want to see more, it just launches nautilus and has it perform the search. Quite useless and broken, in my opinion. Canonical has made the right decision in disabling it al together. Nautilus (file name) search, however has become fast and good (finally after all these years ...).

---

### Post by mfox on 2017-10-28
Thanks for all the replies. I was looking for quick access to recently used files, not a search per se, as I know where these files reside. However, I was wrong about the "recent" gnome shell extension. It does work in Ubuntu 17.10. What threw me off was that opening the file with a wine application (e.g., Microsoft Word or Excel 2010) doesn't register the file in this extension. However, open the same file in LibreOffice apps does register it.

---

### Post by TheFu on 2017-10-28
If this is solved, please mark it so using the **Thread Tools**. This helps others looking for help AND people looking to help.

Ah ... I've never used "Recently Added" for anything.  Always wondered why they bothered.

You can use **find** to find recent files.
```
$ find ~/ -type f -mtime -1
```  though it probably isn't as useful as something showing up in a menu, inside the application you are using.

---

### Post by SeijiSensei on 2017-10-28
I use "recently added" from time to time.  Often I'll have edited an image in GIMP and then need to upload the final product to my WordPress blog.  Using "recently added" avoids searching around the file system for the proper directory.

---

