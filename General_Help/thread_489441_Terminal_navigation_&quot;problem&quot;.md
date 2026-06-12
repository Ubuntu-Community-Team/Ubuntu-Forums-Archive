---
title: "Terminal navigation &quot;problem&quot;"
date: 2007-07-01
forum: General Help
---

### Post by Daveth on 2007-07-01
feeling terribly dense (perhaps my current headache) but how do I navigate in a terminal beyond :

/home/davy/.wine/drive_c/Program Files/ .......

when it consistently refuses to recognise "Program Files" (or all the spelling and spacing variants) as a directory? I have cd Program Files, ProgramFiles, programfiles, Program files, /Program \Files and all the other variations but cannot get beyond. 

Anyone kind enough to point out the corect terminal behaviour?
Thanks

---

### Post by element3260 on 2007-07-01
One of the best terminal shortcuts is autocomplete
You can use it by pressing Tab once you've started typing, for example:
```
cd /home/davy/.wine/drive_c/Pro(Tab) 
```

Will result in: 
```
cd /home/davy/.wine/drive_c/Program\ Files/ 
```

Or if you don't want to remember that just remember that whenever you have a space in a filename, put a \ _before_ the space. 

you can pm me if you need any more help ;)

---

### Post by Daveth on 2007-07-01
and so it does. Very handy.
Many thanks

---

### Post by bettlebrox on 2007-07-01
U gotta escape the white-space with a \ before the white space:

[INDENT]cd Program\ Files[/INDENT]

---

### Post by scooper on 2007-07-01
The other option is quoting the path, i.e. surround it with double quotes and don't use backslash before spaces and other odd characters.  Although I mainly use the quotes in scripts and combine auto-complete and backslashes on the command line.

Quoting example:
```
cd "/home/davy/.wine/drive_c/Program Files/"
```

---

