---
title: "Launcher for text file does not open"
date: 2016-07-16
forum: General Help
---

### Post by 4kh3RAm on 2016-07-16
I created a launcher for a text file, but it will not open.

In other works, when I double click it, nothing happens.

```
/home/andy/Documents/BLANK.txt
```

---

### Post by vasa1 on 2016-07-17
Post the contents of the launcher.

---

### Post by 4kh3RAm on 2016-07-17
I posted the properties.

How do I get the contents of the launcher ?

---

### Post by Keith_Helms on 2016-07-17
A text file is not executable and, thus, can't be launched.  If you want to OPEN the file, you can set the launcher command to **/usr/bin/gedit "/home/andy/Documents/BLANK.txt"** (or whatever text editor you prefer).

---

### Post by 4kh3RAm on 2016-07-17
Thanks.

---

### Post by deadflowr on 2016-07-17
Another simple method, at least with Ubuntu, is to run the command with
*xdg-open*
Which is part of the xdg-utils package, which basically calls forth whatever program is set as the default for whatever file type or url you set as the preferred choice for that file type or url.
Example, if you set mp3's to open with vlc, then 
```
xdg-open my-music-file.mp3
```
will open with vlc.
And if later, you change the default player to open mp3, it'll also change to open that.

As I implied, though, it's a default application in Ubuntu, but I'm not sure about other flavors such as Xubuntu or Ubuntu-Mate.

---

### Post by 4kh3RAm on 2016-07-17
Thanks.

Will save me having to type some long paths.

---

