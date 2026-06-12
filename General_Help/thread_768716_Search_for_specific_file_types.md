---
title: "Search for specific file types"
date: 2008-04-26
forum: General Help
---

### Post by arseniy on 2008-04-26
How do I search a directory for every file of a specific file type? In this case I have a huge directory full of about 50000 subdirectories, and I need to find everywhere an mp3 file appears.

---

### Post by Monicker on 2008-04-26
From a terminal:

find /some/dir -name "*.mp3"

If the dir is really huge, you might want to pipe the results to a text file for easier review:


find /some/dir -name "*.mp3" > mp3s.txt

---

### Post by arseniy on 2008-04-26
Sweet it worked. Thanks!

---

