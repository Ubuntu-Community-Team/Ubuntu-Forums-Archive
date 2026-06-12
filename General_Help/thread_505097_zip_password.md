---
title: "zip password"
date: 2007-07-19
forum: General Help
---

### Post by atlfalcons866 on 2007-07-19
hi
How can i password protect a zip arcive?

---

### Post by yabbadabbadont on 2007-07-19
The built-in encryption provided with zip files is fairly easy to crack, so don't use it if true security is needed.  However, to create an encrypted zip archive, you just need to run the "zip" command in a terminal window and include the "-e" option.  It will prompt you (twice) for the password (the password will not be displayed).

Example: ```
zip -e myzipfile.zip *.jpg
```

---

### Post by atlfalcons866 on 2007-07-19
then what should i use for encryption then?

---

### Post by yabbadabbadont on 2007-07-19
[http://www.gnupg.org/](http://www.gnupg.org/)

Is one way.  It just depends upon how sensitive the information in the zip file is.  If you just want to keep the average person from extracting the file, then the zip password would probably be enough.

---

