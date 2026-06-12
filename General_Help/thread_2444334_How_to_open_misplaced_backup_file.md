---
title: "How to open misplaced backup file"
date: 2020-05-28
forum: General Help
---

### Post by mystmaiden on 2020-05-28
I did something definitely wrong here. I was trying to save a text file but wound up saving it as a backup file apparently. Its pretty important I get the information from the file and save it properly. It landfed in my documents. Is there a way to open this? I cans can see it but I don't know what to use to open it. Any help would be very greatly appreciated.

thanks!

mystmaiden

---

### Post by Impavidus on 2020-05-29
A backup file is not a filetype of its own. It's just a copy of a file, stored under a different name, so that's still a text file.

Can you tell us which application you used to make and save that text file? What files are now present in the directory where you tried to save it? What file format do you mean exactly with text? To me, that means plain, UTF-8 encoded text.

---

### Post by dragonfly41 on 2020-05-29
There are two methods I use currently (and frequently) to scour the filesystem (or target folders) for files I have buried away

The first is to use sudo locate <some-pattern-in-file-name> .. but this requires you to remember the filename or part of it.

The second requires the installation of ripgrep-all but thereafter I can scour for text patterns inside the file. For example find files containing "hello world".  You can use grep pipe to eliminate unwanted files.

There is also the date filter to use since you know the date of the backup?

---

### Post by ajgreeny on 2020-05-29
As you can see it try simply opening it with gedit, mousepad, nano or whichever text editor you use in the OS then save it again with the .txt suffix.

---

