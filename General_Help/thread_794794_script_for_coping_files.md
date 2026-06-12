---
title: "script for coping files"
date: 2008-05-15
forum: General Help
---

### Post by nathangreco on 2008-05-15
Hi I'm new to this forum but I know a little scripting
I'm a sports photographer and i use ubuntu on my laptop to move files off my cameras memory card to the hard drive, 
I would like to make a script to search for all .jpg files within  folders and copy them to another folder I can mount the drive, i think the grep command may be useful but I'm not 100% sure
thankyou 

Nathan

---

### Post by zenwalker on 2008-05-15
Yep grep cmd will help u. Then pipe the output of grep to mv cmd.

---

### Post by sdennie on 2008-05-15
You could try something like:

```

find /source/directory -name "*.jpg" -exec mv {} /dest/directory \;

```

That won't retain the directory structure of /source/directory though.

---

### Post by noynac on 2008-05-15
I use the find command as suggested by vor. You would, of course, want to use cp rather than mv.

The following page has some helpful information on the find command:

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

After copying the JPEG files, I use the same script to rename the files based on their date/time exif data using the exiv2 utility. The command is:

```
exiv2 rename -r "%m-%d-%y@%H:%M:%S" *.*
```

---

### Post by nathangreco on 2008-05-15
Hi the main problem is that my digital camera decides witch folder it stores the files for example
drive
DCIM
1__ (various)PANNA
then the photos po112004.jpg

what I would like to do is search for any .jpg's on the drive and move them to another drive (internal or external)
I may be asking too much of Ubuntu I could never get it working properly on windows XP using dos 

any suggestions?

---

### Post by ibuclaw on 2008-05-15
Use the find command (as above), it searches recursively.

EDIT:
```

mkdir -p ~/Camera && find /media/CANON_DC -name "*.jpg" -exec mv {} ~/Camera \;

```

Regards
Iain

---

### Post by noynac on 2008-05-15
My flash card always mounts as /media/CANON_DC, and I use that as the /source/directory in the script. It will find all JPEG files under /source/directory

---

### Post by ibuclaw on 2008-05-15
I edited my next post, read below.

Copy and paste it into a file, mark is executable and run it.

Then when you open up Nautilus in your home folder, all JPGs will be there in a new folder called "Camera"

Regards
Iain

---

### Post by ibuclaw on 2008-05-15
[EDIT]
OK, here is a complete script for you to work off. It should work for you to a good level of usability.
And I've annotated it so you know what is happening every step of the way.

Where it says "RENAME_ME" replace it with the place where your camera is mounted.
```

#!/bin/bash

checkempty()
{
#While the list of arguments is great than 0.
    while [ $# -gt "0" ]
    do
#If $(ls -A $1) returns true, the folder is not empty
#If it returns false, the folder is removed.
        [ "$(ls -A "$1")" ] && echo "Not Empty" > /dev/null || rmdir "$1"
        shift
    done
}

#Make a directory to store the jpg files.
mkdir -p ~/Camera

#Find the jpg files on your camera.
find /media/**RENAME_ME** -name "*.jpg" -exec mv --backup=numbered {} ~/Camera \; 

#Get a list of all folders on your camera.
camdirs=$(du "/media/**RENAME_ME**" | sed 's/ /*/g' | awk 'NF>2{ $1="";print}{print $2" "}' | tr -d '\n')

#Run the function that checks for empty folders.
checkempty $camdirs

#Change Directory to the jpg folder.
cd ~/Camera

#A small loop to rename "foo.jpg~1~" to a less hidden "foo.jpg(1)"
for i in *
do export j=$(echo "$i" | sed 's/~/(/;s/~/)/')
mv $i $j 2>/dev.null
done

#Finish!

```

Don't underestimate the power of BASH and the Linux Commandline (It is far superior than anything Windows could ever make).
There are many apps that will do everything that you could ever possibly need using the commandline. It's just a case of threading them properly together to make a sweatshirt!

Regards
Iain

---

### Post by nathangreco on 2008-05-16
Thank you tinivole and everyone for your help

---

### Post by ibuclaw on 2008-05-16
Oops, sorry.

That wasn't my fault. It was the PHP Code. :D
It doesn't display backslashes "\"

[PHP]Test test here is a backslash \ You just missed it![/PHP]
```
Test test here is a backslash \ You just missed it!
```
I've changed it, and it should now work.

[http://ubuntuforums.org/showthread.php?p=4968769#post4968769](http://ubuntuforums.org/showthread.php?p=4968769#post4968769)

Regards
Iain

---

