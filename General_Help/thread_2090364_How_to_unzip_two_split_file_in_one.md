---
title: "How to unzip two split file in one?"
date: 2012-12-02
forum: General Help
---

### Post by sinaphysics on 2012-12-02
Hey, I have 2 split file. The names are    'x.wmv.z01'  and  'x.wmv.zip'. When I was in windows I simply choose both file and unzip them, but in ubuntu when I do same I get error which can't unzip the file. How can I make this one Ok?

---

### Post by rnerwein on 2012-12-02
> **sinaphysics said:**
> Hey, I have 2 split file. The names are    'x.wmv.z01'  and  'x.wmv.zip'. When I was in windows I simply choose both file and unzip them, but in ubuntu when I do same I get error which can't unzip the file. How can I make this one Ok?
i don't really know: but i will do following:
1. unzip the first part1
2. unzip the second part2
3. concatonate both by type following command: cat part2 [COLOR=Red]>>[/COLOR] part1
cheers

---

### Post by kostkon on 2012-12-02
> **sinaphysics said:**
> Hey, I have 2 split file. The names are    'x.wmv.z01'  and  'x.wmv.zip'. When I was in windows I simply choose both file and unzip them, but in ubuntu when I do same I get error which can't unzip the file. How can I make this one Ok?
Just right-click on the x.wmv.zip and select to extract it and the archive manager will do the rest.

---

### Post by sinaphysics on 2012-12-02
When I do extract I see this "An error occurred while loading the archive". Maybe the file is corrupted. but I have this problem by other files which I download before too.

---

### Post by gandaran on 2012-12-02
> **sinaphysics said:**
> When I do extract I see this "An error occurred while loading the archive". Maybe the file is corrupted. but I have this problem by other files which I download before too.
check what you have installed for handling zip files
if you haven't these install unzip, p7zip-full and rar.

---

