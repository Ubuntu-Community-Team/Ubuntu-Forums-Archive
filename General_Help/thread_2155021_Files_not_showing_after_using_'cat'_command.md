---
title: "Files not showing after using 'cat' command?"
date: 2013-06-16
forum: General Help
---

### Post by PloXyZeRO on 2013-06-16
For some reason, whenever I use the 'cat' command in terminal to combine two files together, let's say file1.text and file2.txt to make file3.txt, it won't show up in the file manager...but if I compress the folder file3.txt is in, THEN it will show up. I checked "show hidden files" but it still won't show up and I have no idea why. 

I'm using Ubuntu 13.04 64-bit

EDIT: If I use the 'ls' command to list the files in the directory, file3.txt DOES show up, but it does not show up in the file manager for whatever reason

---

### Post by Habitual on 2013-06-16
> **PloXyZeRO said:**
> For some reason, whenever I use the 'cat' command in terminal to combine two files together, let's say file1.text and file2.txt to make file3.txt, it won't show up in the file manager... The exact command please may shed light on the issue, so do post it.

---

### Post by PloXyZeRO on 2013-06-16
First I opened terminal, then typed in
```
cd /home/andrew/Desktop/files
```
I hit enter, then typed this in
```
cat file1.txt file2.txt > file3.txt
```

The strange thing is it actually worked, but I could not view the file at all. It also only happened in that particular folder for some reason. I created a new folder right now and tried it again, and it worked just fine. I'm trying to see if I can recreate the issue to see what happened!

---

### Post by HermanAB on 2013-06-16
Howdy,

Some file managers do not refresh their lists automatically.  This is a very retro kind of bug that showed up again in the last couple years.

Either do a manual refresh or install a better file manager.

---

### Post by PloXyZeRO on 2013-06-17
How do I manual refresh? Also, what other file manager would you recommend? The problem occurred again when I tried to combine a .love file and a .exe file. Again, if I compress the folder, I can see the file, but not in the uncompressed folder.

I followed the instructions here: [http://love2d.org/wiki/Game_Distribution](http://love2d.org/wiki/Game_Distribution)

---

### Post by handheld-penguin on 2013-06-17
F5 usually does it

---

### Post by agillator on 2013-06-17
Your file manager should have a 'View' menu and in there either a 'Refresh' or 'Reload' option or something of that ilk. It may, as handheld-penguin said, show F5 as an accelerator.

---

