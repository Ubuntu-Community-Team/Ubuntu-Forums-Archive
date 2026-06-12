---
title: "How can I edit a text file through the console?"
date: 2006-11-17
forum: General Help
---

### Post by UltraSonicSite on 2006-11-17
Topic^

---

### Post by Ereza on 2006-11-17
You can use nano. An example command would be:

nano file.ext

Then you can edit it and save it using Ctrl+O or exit (it'll ask you if you want to save) using Ctrl+X.

---

### Post by gareththegeek on 2006-11-17
pico is another one

$pico myfile.txt

[http://www.computerhope.com/unix/upico.htm](http://www.computerhope.com/unix/upico.htm)

---

### Post by nikhilk on 2006-11-17
If you are comfortable with Vim use the command
```
vim -X
```

---

### Post by DannyG on 2006-11-17
or to edit a specific file ```
vi *myfile*
``` I prefer VIM myself, takes a bit of getting used to but it gets the job done.

---

