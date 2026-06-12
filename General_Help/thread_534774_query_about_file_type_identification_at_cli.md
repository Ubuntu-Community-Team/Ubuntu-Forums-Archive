---
title: "query about file type identification at cli"
date: 2007-08-25
forum: General Help
---

### Post by DagMan on 2007-08-25
Most file browsers are capable of identifying various file types when they display a file, for example a good file browser such as nautilus is able to tell a text file from a music file from an image file from a video file regardless of file name or file extention.  So if I have files named 1234 and abcd without file extentions the browser is able to tell what type they are.

Can anyone help me out in how I would determine the file type at the command line?

---

### Post by pizzutz on 2007-08-25
```
file <filename>
```


Likely simpler than you expected. :) 

see
```
man file
```
for details

---

### Post by DagMan on 2007-08-25
Yeah that was embarrasingly simple.  Thanks for responding.

---

