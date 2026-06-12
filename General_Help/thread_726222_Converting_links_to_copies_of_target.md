---
title: "Converting links to copies of target"
date: 2008-03-16
forum: General Help
---

### Post by notamonopoly on 2008-03-16
I have several folders with icon sets, each has a number of link files to other images in the same folder. I am wondering if there is a command that I can use to go through the folder and convert each link to a copy of it's target while keeping the same name.

Example: File1 links to File2. Make a copy of File2, delete File1, Rename copied file to File1.

I have no idea how to do this but it would be so much faster to have a script rather than doing it by hand, there are a lot of them.

Thanks

---

### Post by rbprogrammer on 2008-03-16
i'm no expert, but probably not.. you could make a bash script that utilizes commands that will do such an operation.  for instance, use the ls command to get all the files in a directory, then in the script loop through each file testing to see if they are links, eg:
```

if [ -L somefile ]; then 		# is it a symlink ?  
	echo "it's a symbolic link
elif [ -f somefile ]; then 	# is it a regular file ?
	echo "it's a regular file"
fi

```

---

### Post by notamonopoly on 2008-03-16
Thanks for replying.

I have not had the opportunity to write a bash script before, so this is a good learning experience.

Using your example I have this so far:


```
#!/bin/bash

for filename in *.*
do
   if [ -L "${filename}" ]; then 
	echo "${filename} - it's a symbolic link"
   elif [ -f "${filename}" ]; then
	echo "${filename} - it's a regular file"
   fi
done

#End of File
```

So I guess the next step is to figure out how to get the target path from the link, make a copy of the target, delete the link, rename the copied file.

I'm going to keep reading tutorials to figure this out, but any further information you may have would be greatly appreciated.

---

### Post by notamonopoly on 2008-03-16
So I got it working and everything is great now. This saved me so much time.

```
#!/bin/bash

for filename in *.*
do
   if [ -L "${filename}" ]; then
	tempFile=$(readlink "${filename}") #target path
	unlink "${filename}" #delete link
	cp "${tempFile}" "${filename}" #copy target with linkname
   elif [ -f "${filename}" ]; then
	#Regular file - Ignore
	echo "${filename} - it's a regular file"
   fi
done

#End of File
```

---

### Post by rbprogrammer on 2008-03-17
i'm glad i can help you get started, which then lead you to learning bash scripts. :guitar:

---

