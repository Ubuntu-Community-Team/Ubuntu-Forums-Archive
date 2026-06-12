---
title: "Search and replace in text-based files"
date: 2008-06-22
forum: General Help
---

### Post by KenBW2 on 2008-06-22
Is there a command/application that allows me to search for a term and replace it with another across multiple files?
For example, if I had a few CSS, SVG etc files which I wanted to change the background colour for I could search for "background:#FFFFFF;" and replace with "background:#000000;"

---

### Post by sisco311 on 2008-06-22
```
sed -i 's/background:#FFFFFF;/background:#000000;/g' ./*.css
```
[http://en.wikipedia.org/wiki/Sed](http://en.wikipedia.org/wiki/Sed)

---

