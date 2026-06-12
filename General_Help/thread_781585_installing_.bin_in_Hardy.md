---
title: "installing .bin in Hardy"
date: 2008-05-04
forum: General Help
---

### Post by Go_Bucks on 2008-05-04
I am running a java-based gis program called "gvsig". It was working great until I updated to Hardy, which I think is because of change in Java 5. Anyway, I am trying to reinstall the program which installs itself from a .bin. Formerly, after I set the file's permissions to make it executable, you could double click on the file and you would be asked whether you wanted to run the file, run in terminal, or view. Now those options are not present and I get told "there is no application for this file type".

How in the world do I install it?

---

### Post by jocko on 2008-05-04
Make sure the file is executable.

Either run this in a terminal:
```
chmod a+x /path/to/file.bin
```Or right click the file, select properties, then permissions and tick the option "allow running this file as a program".

Edit: I didn't read your post properly, so I missed that you had already set it to be executable.
If you know it's executable, try to run it in a terminal:
```
cd /path/to/file
./file.bin
```

---

### Post by macaholic on 2008-05-04
Have you tried running it directly from a terminal? Do that and post the output.

---

### Post by Go_Bucks on 2008-05-04
I had tried running in terminal with no success, but I didn't realize I needed the "./". That worked... thanks.

What happened to the options to run the program on double-click, though?

---

