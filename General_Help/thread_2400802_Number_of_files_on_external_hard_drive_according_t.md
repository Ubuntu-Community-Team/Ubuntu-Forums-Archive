---
title: "Number of files on external hard drive according to Ubuntu and Lubuntu?"
date: 2018-09-10
forum: General Help
---

### Post by DoktornTheFirst on 2018-09-10
When I check the number of items on my external hard drive on Ubuntu says there is 320 197 **objects** and Lubuntu says there is 320 377 **files**. What is it that Lubuntu counts that Ubuntu doesn't? 

I tried to search for an answer, but had a hard time coming up with good search terms, so here we are. :)

---

### Post by The Cog on 2018-09-10
Folders? Just a quick guess. Symlinks might be another possiblilty. Try creating an empty folder and see which counters change.

---

### Post by DoktornTheFirst on 2018-09-10
The difference seem to lie in how PCManFM (standard file manager on Lubuntu 18.04) and Files (standard on Ubuntu 18.04) count. PCManFM first of always counts hidden files while Files only count them when you show the hidden files and also that when you check a folder for how many files/objects it has PCManFM seem to count the folder itself as one "file" while Files only counts the files and folders in said folder.

---

### Post by The Cog on 2018-09-10
Interesting. 
Thunar (the default Xubuntu file manager) counts 1 for the folder itself and always counts hidden files. It reports "items", not "files".

---

