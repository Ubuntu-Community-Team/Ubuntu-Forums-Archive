---
title: "find files in dir based on text in file"
date: 2008-03-30
forum: General Help
---

### Post by andersl on 2008-03-30
Hi

I have a text file containing text similar to

4365
4378
4387
3488

I have a dir with files named DSC_4365.jpg or DCS_4333 i.e. so the four digits in each line from the text file should identify a specific file in the dir. I'd like to make a little script that copys the files specified from the text file to another dir, but I dont know how :( can any of you help me ?!

Thanks

---

### Post by .nedberg on 2008-03-30
```
#!/bin/bash
pre=DSC_
suf=.jpg
for i in $(cat nr.txt); do
	echo $pre$i$suf
done
```

will give you the filenames. Fill in with source- and destination folder and copy the files with cp

---

