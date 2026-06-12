---
title: "BASH recursive directory search"
date: 2008-06-08
forum: General Help
---

### Post by alistair77 on 2008-06-08
Hi,

I have thousands of photos in hundreds of folders. Some directories contain sub folders containing more photos.  What's a simple shell script for recursively looking in each folder and sub-folder and copying any .jpg and .mpeg files to a new directory?

Thanks

---

### Post by ad_267 on 2008-06-08
So you want all of the photos to go into the same directory? Try something like this:

```

#!/bin/bash
find /home/user/foldertosearch -name *.jpg -type f -exec cp '{}' /home/user/foldertocopyto/ \;
find /home/user/foldertosearch -name *.mpeg -type f -exec cp '{}' /home/user/foldertocopyto/ \;

```

---

### Post by alistair77 on 2008-06-08
Thanks.  This works perfectly.  

I've just realised that some of the source files have duplicate names and this command is overwriting one file with another.  Is there a way of saying; 

if file to be copied exists in destination folder, then create copy and name it filename-1?

or perhaps always prefix the file name with the source folder name?

---

### Post by ad_267 on 2008-06-08
OK this script should do what you want. If a file of the same name already exists it adds a 1 on the end and if that exists it adds a 2 etc.

```

#!/bin/bash

SEARCHDIR=/home/user/search_directory
DESTDIR=/home/user/destination_directory
EXTS=(jpg mpeg)

for EXT in ${EXTS[@]}
do
	COUNTER=0
	for file in $( find $SEARCHDIR -name "*.$EXT" -type f )
	do
		BASENAME=$(basename $file .$EXT)
		FILENAME=$BASENAME
		while [ -e ${DESTDIR}/${FILENAME}.$EXT ]
		do
			COUNTER=$[$COUNTER+1]
			FILENAME=${BASENAME}${COUNTER}
		done
		cp $file ${DESTDIR}/${FILENAME}.$EXT
	done
done
```

---

### Post by alistair77 on 2008-06-08
Cheers. This works great.  Thanks for your help

---

### Post by nick_h on 2008-06-08
> **ad_267 said:**
> So you want all of the photos to go into the same directory? Try something like this:

```

#!/bin/bash
find /home/user/foldertosearch -name *.jpg -type f -exec cp '{}' /home/user/foldertocopyto/ \;
find /home/user/foldertosearch -name *.mpeg -type f -exec cp '{}' /home/user/foldertocopyto/ \;

```

You should really put some extra quotes in the name options.
```
find /home/user/foldertosearch -name **"***.jpg**"** -type f -exec cp '{}' /home/user/foldertocopyto/ \;
```

I see you did in your next post. :)

---

