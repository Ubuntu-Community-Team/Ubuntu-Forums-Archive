---
title: "Ubuntu thinks pen drive full"
date: 2008-03-25
forum: General Help
---

### Post by lowebb on 2008-03-25
I have a 4gb pen drive which Unbuntu seems to think is full. On Vista there is 3Gb free but a "df -h" shows the pen drive to be completely used. 

any ideas why this is and more importantly how to fix it?

---

### Post by Lord Illidan on 2008-03-25
Check if there is a .Trash folder. In Nautilus, press CTRL + H to view hidden files, and it should be there. To permanently delete files from your drive, you should use SHIFT + DEL, not just DEL, as that puts them in the .Trash folder.

---

### Post by lowebb on 2008-03-25
I'm pretty sure I did a 'ls -al' which should show hidden files as well but I'll definitely give this a go tonight

---

### Post by milton1 on 2008-03-25
There may also be a trash folder from windows, which ubuntu may show as space in use.

---

