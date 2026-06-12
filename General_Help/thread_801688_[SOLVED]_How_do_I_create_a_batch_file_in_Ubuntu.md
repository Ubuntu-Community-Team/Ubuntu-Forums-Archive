---
title: "[SOLVED] How do I create a batch file in Ubuntu?"
date: 2008-05-20
forum: General Help
---

### Post by Rytron on 2008-05-20
Hi,
I seen a great tutorial for creating a batch file in Windows that will create a list of every file on your pc. The code was this:

[B]```
dir /s *.* >dirlist.txt
```
save as listing.bat
encoding: ANSI[/B]

[I]What code in Ubuntu would do the same job?
Thanks.[/I]

---

### Post by lisati on 2008-05-20
The Linux equivalent of a batch file is called a "Shell script"

---

### Post by tamoneya on 2008-05-20
in linux you call them shell scripts instead of batch files.  In this case it is ```
ls -R / > dirlist.txt
```

---

### Post by Rytron on 2008-05-20
> **tamoneya said:**
> in linux you call them shell scripts instead of batch files.  In this case it is ```
ls -R / > dirlist.txt
```

Thank you tamoneya,
I amended your code to ```
sudo ls -R / > dirlist.txt
```

This way I don't get all those Permission denied messages in the terminal.
Cheers.

---

### Post by Rytron on 2008-05-20
That code is awesome. How about code to for example make a list _only_ of all files on the Desktop including all folders on the Desktop?

---

### Post by MythosLegend on 2008-05-20
You mean like
```
ls -R ~/Desktop > dirlist.txt
```
?

---

### Post by tamoneya on 2008-05-20
just change the "/" to what ever directory you want to list. ls -R ~/Desktop > list.txt will do the desktop.  ls -R /etc > list.txt will list all the files in /etc.  Im sure you can figure it out from there.

---

