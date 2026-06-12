---
title: "chmod only for files"
date: 2007-02-11
forum: General Help
---

### Post by Hakimio on 2007-02-11
How do I change permissions only for files leaving folder permissions intact?
I know **find /<top-level-directory>/* -type f | xargs chmod "g+w"** command but it throws me an error every time it encounters file or folder with spaces in their names :(

---

### Post by meng on 2007-02-11
What about something like:
for name in `find /toplevel/* -type f`; do chmod g+w "$name"; done

---

### Post by Hakimio on 2007-02-11
Says: **chmod: cannot access** every time it finds file/folder with spaces :(

---

### Post by astoltz on 2007-02-11
This is from the xargs man page:
> Because Unix filenames can contain blanks and  newlines,  this  default behaviour is often problematic; filenames containing blanks and/or new&#8208;lines are incorrectly processed by xargs.  In these  situations  it  is better  to  use  the  &#8216;-0&#8217; option, which prevents such problems.   When using this option you will need to ensure that the program  which  pro&#8208;duces  the  input  for xargs also uses a null character as a separator.  If that program is GNU find for example, the &#8216;-print0&#8217; option does this for you.


---

### Post by Qew on 2007-02-11
Use what's below (the full stop indicates that you want to start the find from the current directory, while 644 is just an example chmod; use the appropriate number for what you want to do):

find . -type f -exec chmod 644 {} \;

---

### Post by Hakimio on 2007-02-11
> **Qew said:**
> Use what's below (the full stop indicates that you want to start the find from the current directory, while 644 is just an example chmod; use the appropriate number for what you want to do):

find . -type f -exec chmod 644 {} \;
Thanks, it worked :)

---

