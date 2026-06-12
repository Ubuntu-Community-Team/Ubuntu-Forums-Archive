---
title: "For Statement"
date: 2008-06-23
forum: General Help
---

### Post by pjpalmq on 2008-06-23
Greetings.

I have a directory which contains scan01.jpg through scan103.jpg.  I also have another directory which contains scan01.jpg through scan50.jpg.  I would like to merge the two directories but know that I have to first rename all the files in the second directory prior to merging so as not to over-write anything.

I know it is possible to use the for command to do rename the files but need the syntax.

Anyone have the answer?

Best,
Peter

---

### Post by ibutho on 2008-06-23
One option is 
```
for i in `ls`; do mv "$i" new_file;done
```
I am sure you can further refine that, but I am not much of a programmer so I will let you figure that one out. Alternatively you can use a batch renaming tool like krename (don't know of a gnome specific tool).

---

### Post by ad_267 on 2008-06-23
There's the rename command which uses perl regular expressions

This will show you what will actually be renamed but won't actually do the renaming:
```
rename -n "s/scan/scan_two/" *
```

This will do the renaming:
```
rename -v "s/scan/scan_two/" *
```

---

### Post by pjpalmq on 2008-06-23
I would like to rename all of the files in the second directory incrementally from where the first directory stopped. Is that possible?

---

### Post by kaibob on 2008-06-24
I am just learning shell scripting, and I suspect there is an easier way to do this, but the following works:

```
#!/bin/bash
filenumber=104
for file in *.jpg ; do
mv $file scan$filenumber.jpg
filenumber=$((filenumber + 1))
done
```

You have to change to the directory containing the files to be renamed before executing this script. You could substitute $1 for 104 and enter the beginning filenumber as a commandline argument.

---

### Post by pjpalmq on 2008-06-24
kaibob,

Thanks so much!  Works GREAT!  The only thing I wish I could have done was to maintain the four place number scheme as the subsequent ls displays them differently than I would like.  Your shell scripting was wonderful though!

Best

---

### Post by pjpalmq on 2008-06-24
ibutho,

Thanks for the tool krename!  I had never heard of it before, and will absolutely use on another project I have.

Regards,

---

