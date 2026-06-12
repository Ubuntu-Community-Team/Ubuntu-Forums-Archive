---
title: "find: ‘/run/user/1000/gvfs’: Permission denied"
date: 2017-09-07
forum: General Help
---

### Post by raleigh3 on 2017-09-07
Getting this error.

```
andy@7:~/Downloads$ sudo find / -name *.png >> png_files.txt
[sudo] password for andy: 
find: ‘/run/user/1000/gvfs’: Permission denied
```

---

### Post by TheFu on 2017-09-09
Try:
```
~/Downloads$ sudo find / -name \*png >> /tmp/png_files.txt
```

two things.
a) the regex needs to be escaped.  wildcard expansion happens BEFORE the command is called on Unix shells, unlike in Windows. Plus the rules are different.
b) the appended file needs to have permissions somewhere as the current userid.

The 'find' runs as root.
The >> runs as the non-sudo userid.  There are 2 processes involved, not 1 in that command.

Another way is
```
~/Downloads$ sudo find / -name \*png |tee -a /tmp/png_files.txt
```
This will let you see the output AND have it appended to the file.  I like 'tee'.  And neither of these commands will put errors, usually written to stderr, into the file. 

Good luck.

---

