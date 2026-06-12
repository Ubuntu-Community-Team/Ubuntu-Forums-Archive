---
title: "Search inside files"
date: 2008-06-13
forum: General Help
---

### Post by randomAccess on 2008-06-13
The picture shows search options in windows explorer and the parameter "search a word or phrase inside the file"

[[IMG]http://img117.imageshack.us/img117/3824/snap1im0.th.png[/IMG]](http://img117.imageshack.us/my.php?image=snap1im0.png)

Is there a program in Linux that has the same option? I tried this in nautilus, but it can only search names and extensions. Maybe a standalone application?

The problem may occur as I usually search inside different document from .txt files to .doc, docx and presetations. 

I also tried to achieve this by using grep but with no success.

---

### Post by angry_johnnie on 2008-06-13
You could

```
grep -Rs some-title-or-text /some/directory/*
```

where 'some-title-or-text' is whatever you might be looking for, and '/some/directory/' is the directory you want to be looking in.

the **R** option makes it recursive, and the **s** will suppress any error messages about non-existent files or directories.

---

### Post by NilsE on 2008-06-13
Try 

Application > Accessories > Search tool

It may not have indexed by default so go into 

System > Preferences > Search and Indexing

and set it for the options and the folders you want to include and let it index.

---

### Post by randomAccess on 2008-06-13
Thanks for the appropriate grep syntax :)

also thanks for the gui tool. actually the tool was in the task bar in my ubuntu and I didn't see it.

---

### Post by joshsmith on 2008-06-13
you can also do
places>search for files
select more options
and add the option
"contains the text"

---

### Post by MacAnthony on 2008-06-13
Or install beagle if you do this a lot.
[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)
[http://beagle-project.org/Main_Page](http://beagle-project.org/Main_Page)

---

### Post by randomAccess on 2008-06-14
Thanks it helps a lot. 

I read that Beagle is faster than Ubuntu's serach tool, but Beagle doesn't have an option "search inside file" so it's of no use to me.

---

### Post by dbera on 2008-06-14
> **randomAccess said:**
> Thanks it helps a lot. 

I read that Beagle is faster than Ubuntu's serach tool, but Beagle doesn't have an option "search inside file" so it's of no use to me.

:confused: Wait what ?! What makes you think that ?
[http://beagle-project.org/About](http://beagle-project.org/About)

---

### Post by randomAccess on 2008-06-14
> **dbera said:**
> :confused: Wait what ?! What makes you think that ?
[http://beagle-project.org/About](http://beagle-project.org/About)

by entering string search from Excel file and Beagle didn't find it ;)

---

### Post by dbera on 2008-06-14
> **randomAccess said:**
> by entering string search from Excel file and Beagle didn't find it ;)

I see ... well, from [http://svn.gnome.org/viewvc/beagle?rev=4773&view=rev](http://svn.gnome.org/viewvc/beagle?rev=4773&view=rev) on Jun 2, 2008:
> Since gnumeric svn r15294, ssindex writes the first two diagnostic lines when run as "ssindex -i" to stderr instead of stdout. As a result, ssindex based spreadsheet filter broke in Dec-06 !!!

so I guess its a bug :-)

---

