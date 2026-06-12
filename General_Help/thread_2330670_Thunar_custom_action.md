---
title: "Thunar custom action"
date: 2016-07-13
forum: General Help
---

### Post by 4kh3RAm on 2016-07-13
Trying to make a thunar custom action that zips files. 
 
This is not working. 
 
Anyone know why ? 
 [TABLE="width: 90%, align: center"]
[TR]
[TD][/TD]
[/TR]
```
[TR]
[TD="class: code"]
zip -u %f 
[/TD]
[/TR]
[/TABLE]

```

---

### Post by LewisTM on 2016-07-13
You need to specify the target zip file.
I would suggest the following syntax: 
```
zip -u %n.zip %F
```
This will zip all selected files and create a zipfile using the name of the first file, with .zip appended.

Cheers!

---

### Post by 4kh3RAm on 2016-07-13
> **LewisTM said:**
> You need to specify the target zip file.
I would suggest the following syntax: 
```
zip -u %n.zip %F
```
This will zip all selected files and create a zipfile using the name of the first file, with .zip appended.

Cheers!

Thanks.

It does quite work as intended.

It zipped up file I selected but also zipped up 2 other directories.

I will work on the syntax.

I tried, but no luck.

> **-D**  
 Do not create entries in the *zip*  archive for directories.  Directory entries are created by default so that their attributes can be saved in the zip archive. The environment variable ZIPOPT can be used to change the default options. For example under Unix with sh: 


---

### Post by LewisTM on 2016-07-14
The directories are probably reconstructed from paths included with the zipped filenames.
Try this :

> -j
--junk-paths
   Store just the name of a saved file (junk the path), and do not store directory names. By default, zip will store the full path (relative to the current directory).

---

### Post by 4kh3RAm on 2016-07-14
Thanks.
It worked perfectly.

---

