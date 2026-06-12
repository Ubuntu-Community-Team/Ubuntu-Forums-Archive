---
title: "modify text"
date: 2013-04-28
forum: General Help
---

### Post by Icebear on 2013-04-28
I am trying to change a txt file to simple html file.

By using sed I made a very good start. but I have one problem.
With headings I need to some add </h2> at the end of the line which now start with <h2>

So is there a way for sed or some other command to locate <h2> and then add </h2> after the text at the end of the line.

---

### Post by Impavidus on 2013-04-28
```
sed 's/<h2>.*$/&<\/h2>/' oldname >newname
```
This assumes the </h2> isn't present in any of the lines yet.

---

### Post by Icebear on 2013-04-29
Thank you Impavidus. That was great. just what I needed.

---

