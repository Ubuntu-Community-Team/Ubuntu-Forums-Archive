---
title: "Batch extract large number (836) of zips?"
date: 2007-02-15
forum: General Help
---

### Post by m4gnesium on 2007-02-15
I have 836 zip files in a folder I would like to extract. The obvious solution of select all -> right click -> extract here didn't work very well. Only a handful extracted, I guess the rest of the processes hung. Is there a way to do a batch extract on each file in sequence? I'd rather not have to manually extract all 836 of them.

I'm running Kubuntu if it makes any difference.

---

### Post by raja on 2007-02-15
I would think the easiest way to do it from the terminal is to 'cd' into the directory and then 'unzip *.zip' there. You should also be able to see a message if unzipping fails for a file.

---

### Post by m4gnesium on 2007-02-15
No luck. The output looks like this:
```

caution: filename not matched: file1.zip
caution: filename not matched: file2.zip
...

```
and so on down the whole list.

---

### Post by m4gnesium on 2007-02-15
Solved it. the *.zip needed quotes around it. Thanks for the tip!

---

