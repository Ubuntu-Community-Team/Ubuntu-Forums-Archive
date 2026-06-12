---
title: "list all files of type?"
date: 2007-12-06
forum: General Help
---

### Post by buccaneere on 2007-12-06
What's the command to list all files of type **.ts** ?

Thanks.........

---

### Post by davidgarcin on 2007-12-06
ls *.ts

---

### Post by buccaneere on 2007-12-06
> **davidgarcin said:**
> ls *.ts

Thanks!

I got no return for that command. Does that mean I have no files of type .ts ?

I tried this: ls /* , and got a bunch of stuff. Is this all of the files on this box?

If not, what is it? What is the command to list all files?

---

### Post by lvleph on 2007-12-06
That command is dependent on where you run it. If you go into palces and then clcik search, you can do a search for *.ts.

---

### Post by erfahren on 2007-12-06
try using the "find" command

pages that might help get you started:
[http://www.kingcomputerservices.com/unix_101/using_find_to_locate_files.htm](http://www.kingcomputerservices.com/unix_101/using_find_to_locate_files.htm)
[http://lowfatlinux.com/linux-find-files.html](http://lowfatlinux.com/linux-find-files.html)
[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by davidgarcin on 2007-12-06
Sorry, I didn't realize you were trying to search your whole computer.

In this case, it's better to use the find command:
```
find / -name '*.ts'
```
find is the name of the command, / tells it to search at the root of the file system, -name '*.ts' tells it to search for any file ending in .ts

ls *.ts would list all the .ts files in your current directory.
ls /* would list all files and directories under root (the beginning of the file system)

That should do you :-).

---

### Post by stroyan on 2007-12-06
The slocate package can improve the speed of file searches.
```
find / -name '*.ts'
``` will need to walk through every directory.
That will be rather slow.  (But it will get faster when repeated because of caching.)
The slocate package builds a database of file names that it can reuse rapidly.
It normally updates the database once a day.  You can update it again with
```
sudo updatedb
```
Then you look for file names with the locate command like ```
locate '*.ps'
```
Both find and locate will give different results when run as a normal user or as sudo to root.
Some directories are not readable by all users.

---

### Post by buccaneere on 2007-12-06
Excellent info from all!

Gotta' add this thread to favorites... Many pc mags have articles about file search tools for windows; file searching linux probably needs comparable tools/tips columns???

---

