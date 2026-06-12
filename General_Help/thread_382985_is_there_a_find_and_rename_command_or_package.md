---
title: "is there a find and rename command or package?"
date: 2007-03-12
forum: General Help
---

### Post by dimeotane on 2007-03-12
I've got a hundred or so files of the same name located in different directories, that I need to move to a new folder.  How can I do this?  It looks like they all need to have different names? 

When I locate them by using the search in nautilus and then drag and drop to a new directory, it only copies over one.  If I try to copy another it gives me the option to skip or replace.  Now obviously I'm not going to rename them all by hand, so what does one do?  I've looked for a package that could do it, but didn't find much. 

Shouldn't nautilus be able to simply paste them in and rename the similarly named file with a (1) or (2) behind it?

I've read about using the terminal command "find", and it seems capable enough.  But right now it only will end up copying one, until I can get it to rename each file differently.  How can I fix this command to rename each duplicate "file.db" differently:
```
  $ find /home/dell/large-data-files/ -name file.db -exec mv -b  {} ~/Desktop/test  \;
```

If I have to rename them all first, what command could I use to locate all files on the hard drive that have the name file.db and rename each one different.

---

### Post by finer recliner on 2007-03-12
take a look at "bulk rename". it comes with xubuntu. it may be what you're looking for.

---

### Post by denver on 2007-03-12
> **finer recliner said:**
> take a look at "bulk rename". it comes with xubuntu. it may be what you're looking for.

if that doesent help, i have written a small script that will ask you for the filename folder to search and destination folder. it will locate any file with that name and copy it to a folder of your choice with a prefix at the end. The new files created will be named the same as the original, but with a number at the end (  file.db.1 file.db.2 file.db.3 and so on for each file )

here is the code:

> 

#!/bin/bash


COUNT=0

echo -n "Please enter the filename&#57344;you wish to search for: "
read filename
echo -n "Please specify the folder you wish to scan: "
read location
echo -n "Please specify a destination folder for the files: "
read destination

if [ ! -d $location ]
then
        echo "The folder you specified does not exist"
        exit 1
fi

if [ ! -d $destination ]
then
        echo "The folder you specified does not exist"
        exit 1
fi


LOCATE=`find $location -name $filename`


for i in $LOCATE
do
        while [ -f $i ]
        do
                cp $i $destination/$filename.$COUNT
                let COUNT+=1
                break
        done
done




Just copy this in a file, flag it as executable and fire it up in a terminal. Don't forget to use absolute paths for the folder you wish to scan, as well as for the destination  folder.

---

### Post by stylishpants on 2007-03-12
Here's a quick and dirty solution:


 find /home/dell/large-data-files/ -type f -name file.db | while read f; do i=`stat -c '%i' $f`; cp $f ~/Desktop/test/file.db-$i; done

It appends the file's inode number onto the name of the copied file.  Note that this is copying, not moving.  Just change cp to mv if you really want to mv the files.

---

### Post by mexlinux on 2007-03-12
Install krename it is able to what you want

---

