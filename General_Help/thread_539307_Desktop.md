---
title: "Desktop"
date: 2007-08-31
forum: General Help
---

### Post by doctorbrowder on 2007-08-31
A simple question, but one I can't figure out... 

In the terminal window, how do I get to the desktop??? I tried just "cd desktop" but that doesn't seem to work. I have a printer driver there I need to install, but I can't figure out how to tell the terminal where to find it.

Thanks!

---

### Post by hallbrian on 2007-08-31
You could just move the file to your home folder. but here is where you will find your desktop.

```
cd /home/you/Desktop
```

Brian

---

### Post by kesman on 2007-08-31
remember that the directory names are case sensitive, its Desktop, not desktop. You can easily see all the subdirectories in a dir by first typing cd and then pressing tab one ore more times, as it tries to "guess" what you're next going to type, so you could type cd and D and then press tab and it will automatically then add the remaining characters into the directory name.

---

### Post by vanadium on 2007-08-31
Even shorter:

cd ~/Desktop

~ expands to your homedirectory.

Even quicker: type

cd ~/De<tab>

and the tab key will expand the full name.

---

### Post by kesman on 2007-08-31
exactly

---

