---
title: "What are &quot;all/all&quot; and &quot;all/allfiles&quot;"
date: 2017-07-18
forum: General Help
---

### Post by spencer2 on 2017-07-18
So, for a while when I run updates & stuff, there are these 2 files that my terminal slows down processing so I can read them nicely... they are: 

unknown media type in "all/all
and then the same message except in file "all/allfiles"

does anyone know what this is please & thank you?

---

### Post by #&amp;thj^% on 2017-07-19
These are really harmless, you probably have added a PPA that has not updated your "mime" files.
Give this a shot and report back any errors here,
```
sudo update-mime-database /usr/share/mime
```
The above command will take some time to complete so don't worry if it looks like it is stuck.

---

