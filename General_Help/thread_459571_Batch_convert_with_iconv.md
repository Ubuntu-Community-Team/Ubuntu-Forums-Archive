---
title: "Batch convert with iconv"
date: 2007-05-30
forum: General Help
---

### Post by theseeker on 2007-05-30
Hi,

I have a bunch of .srt files that need to be converted from iso8859-7 to utf-8 with iconv. Is there an easy way to do that without manually typing each filename? The restriction is that I need to keep the same filename for every file. 

Thank you!

---

### Post by raja on 2007-05-30
It should be something like this - 
```
cd /folder containing files
for file in *.txt
 do
  iconv -f iso8859-7 -t utf8 "$file"
 done
```

---

### Post by theseeker on 2007-05-30
Is that a bash shell script? Are there any semicolons/backslashes missing? Please provide a working solution as I'm not really into shell scripting to correct the syntax. Thanx!

---

### Post by raja on 2007-05-30
It should work as it is. 
However the first line is 'pseudo code'. You have to 'cd' (change directory) to the folder where your files are.
I would recommend making a test folder with about 3-4 files and running this - if it works ok, run it in the main folder.

---

