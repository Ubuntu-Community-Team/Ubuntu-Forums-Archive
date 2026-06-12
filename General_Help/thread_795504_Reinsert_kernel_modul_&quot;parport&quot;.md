---
title: "Reinsert kernel modul &quot;parport&quot;"
date: 2008-05-15
forum: General Help
---

### Post by ario on 2008-05-15
Hi
I have removed kernel modul "parport" from my ubuntu 8.04 amd64 by running command:
```

sudo rmmod parport

```

Now i don't now how to insert this modul again. Running command "insmod parport" results:
```

# insmod parport
insmod: can't read 'parport': No such file or directory

```
Any idea?
Thanks a lot for your helps:)

---

### Post by jamessnell on 2008-11-09
try: 

modprobe parport

---

