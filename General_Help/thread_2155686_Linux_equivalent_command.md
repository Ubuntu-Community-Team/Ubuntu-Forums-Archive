---
title: "Linux equivalent command?"
date: 2013-06-19
forum: General Help
---

### Post by cimmo1 on 2013-06-19
G'day, in the world of the 'other OS' (Win/DOS) I frequently used this command line (run from the desired folder directory):

tree /f /a >c:\test.txt

This produced a text file containing a folder+file list of the contents of an drive or folder.

Is there a simple equivalent terminal command in linux that would do the same thing?

Thank you.

---

### Post by Cheesemill on 2013-06-19
```
tree -f -a > test.txt
```

I can't remember if the tree program is installed by default. If you don't have it it can be installed by doing...
```
sudo apt-get install tree
```

---

### Post by cimmo1 on 2013-06-19
Thank you. Works well.

---

