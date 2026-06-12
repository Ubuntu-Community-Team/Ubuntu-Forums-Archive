---
title: "Application Install Directory"
date: 2005-07-24
forum: General Help
---

### Post by migo on 2005-07-24
I installed opera, and while I can run it I can't find where it is located, so I can't create a quick launch for it with the proper icon. What directory are applications usually installed to?

---

### Post by frodon on 2005-07-24
Usually applications are installed in your /home/user directory, i think for you in /home/user/.opera. Installed application are always hidden, they start with "." caracter.
To see hidden file : "ls -a" in a terminal in your user directory or Ctrl + h in nautilus.
Generally if you want to locate a file do as follow : ```
sudo updatedb
locate file_name
```updatedb create a database of all the path and locate command allow you to search in this database (it works even if you don't have the full name of the file)

---

