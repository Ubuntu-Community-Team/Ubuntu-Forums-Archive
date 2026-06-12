---
title: "Whats up with the ctrl+f search in nautilus"
date: 2008-03-06
forum: General Help
---

### Post by aashay on 2008-03-06
Is it just me or does the search box (ctrl+f) in Nautilus almost never work? For example, I have a directory ActivePython in the home directory, and more matches a few folders in. Searching for "python" in it gives a torrent 2 folders deep. This torrent is the ONLY match returned. Is the search suppoed to work this way? Sometimes the search returns files with no resemblance to the search term whatsoever.  A search for "sso" returned "Moe.pdf". Is there something I am missing here?

---

### Post by sillyxone on 2008-03-06
yeah, it's pretty much broken, especially if you don't have Tracker on (even with Tracker, it searches by file contents instead of filename)

what I did is assign Super-F to command "gnome-search-tool", which searches by filename

---

### Post by aashay on 2008-03-07
Thats what I use too. Just thought there would be a better way of searching for things in the pwd. Setting the correct folder in the search tool takes a few extra clicks :p

---

### Post by ryanhaigh on 2008-03-16
There are workarounds for this such as places > find files. You can also install nautilus-search-tool which provides a right click option to search the directory using the gnome-search-tool. I have also written a howto on recompiling nautilus without tracker support, it is not as hard as it may sound.
[http://ubuntuforums.org/showthread.php?p=4524522](http://ubuntuforums.org/showthread.php?p=4524522)

---

