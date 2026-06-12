---
title: "Compressing directories into CD-sized chunks for backup..."
date: 2007-05-15
forum: General Help
---

### Post by Cheese Sandwich on 2007-05-15
What command-line methods do you use?

---

### Post by MoLE on 2007-05-23
Hi Cheese,

I usually compress the directories I want using tar into a single tar.gz file, then use the ```
split
``` command.  I'd have to read the man page to get the syntax, though.```
$ man split
```

---

### Post by orb9220 on 2007-05-23
also [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) partimage will allow you to set chunk sizes I believe.

---

### Post by shad0w_walker on 2007-05-23
Be warned about partimage, the only way i am aware of to get data back from its images is to restore the complete image to a partition atleast the size of the original one. Its fine for doing a full system back up (I use it for mine) but if you need to easily access single files/folders with restoring everything it is not a good tool for you.

---

