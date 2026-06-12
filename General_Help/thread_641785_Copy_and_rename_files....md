---
title: "Copy and rename files..."
date: 2007-12-15
forum: General Help
---

### Post by smartboyathome on 2007-12-15
Would there be a way to copy files from one directory to another and then have every file's name to be appended with a prefix?

Thanks for the help!
Smartboy

---

### Post by eapache on 2007-12-15
As in, any file copied to that directory gets the prefix?

---

### Post by smartboyathome on 2007-12-15
Yeah (like files a, b, and c get copied into directory d and gets a prefix g-a, g-b, and g-c.

---

### Post by eapache on 2007-12-16
I can't think of any way to do it automatically for any file (there probably is one, I just don't know what it is), but I'm sure somebody could write a script which copies and renames any files it is passed.

---

### Post by jken146 on 2007-12-16
Thunar has a bulk-rename utility that comes installed with Xubuntu (not sure what the package is).  It lets you do that sort of thing with filenames.

---

### Post by dagnabit dang doohickey on 2007-12-16
This command will copy all the files in the root level of the source directory to the destination directory and all the copies will have filenames prefixed with *PREFIX*.
```

cd source/ && find * -maxdepth 0 -type f -exec cp -v {} ~/destination/PREFIX{} \;

```

---

### Post by smartboyathome on 2007-12-17
Thank you all, I got it now. :)

---

