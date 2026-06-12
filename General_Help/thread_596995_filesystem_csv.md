---
title: "filesystem csv"
date: 2007-10-30
forum: General Help
---

### Post by Tekno_Cowboy on 2007-10-30
I'd like to make a delimited text file of an entire drive that lists all filenames seperated by folder, and can be imported into a spreadsheet.
Any Ideas?

---

### Post by devilears on 2007-10-30
not sure i understand, but what about:
ls -la -R > file.csv  ?

---

### Post by Tekno_Cowboy on 2007-10-30
Could you please tell me what that is supposed to do? I'm not alltogether familiar with linux commands.

---

### Post by nick_h on 2007-10-31
ls is a command that lists files.  It is being run with 3 options:

-a lists all files including hidden files starting with a "."
-l outputs in a long format
-R means recursive - descends down directory trees

The output is then re-directed to a file.  It won't do any harm so give it a try.

For more details look at the manual page:
```
man ls
```

If this doesn't do what you want then try using "find" as follows:
```
sudo find / -print > files.txt
```

---

### Post by Tekno_Cowboy on 2007-11-04
Thanks, I wound up using sudo ls */*/ > current.txt, which I figured out from your suggestions.

---

