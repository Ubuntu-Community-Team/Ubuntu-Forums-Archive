---
title: "How to search of a directory?"
date: 2016-01-14
forum: General Help
---

### Post by Evil Wayz on 2016-01-14
I just saved a picture into a sub dir of Pictures.  THere were five other pictures in that directory.  I went to add another picture to the sub dir and it is gone.  I  can't remember the name of any of the pictures in there.  Recent files option doesnt come up with anything, and searching for hte file finds it in PIctures.  THis happened to me once before and the folder had been arbitrarily moved inside another folder.  Can't remember how I figured that out, so any help would be appreciated.  I'm trying to loace a directory, not a file.

Using 14.04, with gnome flashback.

---

### Post by sandyd on 2016-01-14
Navigate to the pictures folder in the terminal and use 
```

find . -type d -name "*mydirectory*"
```
where *mydirectory* is the name of the folder.

---

### Post by vasa1 on 2016-01-15
Or maybe this:```
11:50 AM ~/Pictures $ find . -type d
.
./Screenshots
./Colors
./Colors/html_colornames.asp_files
./Unwanted_icons
./smplayer_screenshots
11:50 AM ~/Pictures $ 
```

---

### Post by Evil Wayz on 2016-01-15
THis gets no output, so wherever it went off to, it's not inside Pictures anymore. I used the right click menu to copy the picture, is it possible I accidentally moved the whole folder somewhere?

---

### Post by sandyd on 2016-01-16
Try searching in your home folder.

---

