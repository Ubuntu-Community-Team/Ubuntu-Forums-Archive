---
title: "copy random files overwrite or rename"
date: 2016-10-05
forum: General Help
---

### Post by sohlinux on 2016-10-05
I want to copy 1000 random files from a folder and sub folders with many 1000s of files but some of the files have the same name and it prompts me to overwrite but how can I let it over write automatically or rename the file if the file has the same name?

I am using the following
```
cp $(find . -iname "test*.ext" -print | shuf -n 100) /home/user/rand
```

thanks

---

### Post by Keith_Helms on 2016-10-05
To overwrite a duplicate filename
```
cp -f $(find . -iname "test*.ext" -print | shuf -n 100) /home/user/rand
```

To rename a duplicate filename
```
cp --backup=numbered $(find . -iname "test*.ext" -print | shuf -n 100) /home/user/rand
```

---

### Post by steeldriver on 2016-10-05
For whitespace safety, I can't help feeling you should be using something more like

```

find . -iname "test*.ext" -print0 | shuf -zn 100 | xargs -0 cp -t /home/user/rand

```

(adding either the `-f` or `--backup=numbered` option as described by Keith_Helms)

---

### Post by colmax on 2016-10-06
Some graphic file managers will ask if you want to over-write all or one instance
Cheers

---

### Post by sohlinux on 2016-10-06
thanks for the answers. they work fine :)

---

