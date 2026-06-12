---
title: "Help with filename compare in bash script"
date: 2008-01-17
forum: General Help
---

### Post by lucient on 2008-01-17
Hello i am trying to compare filenames between 2 folders and the matching file name will be moved to a different location. I think i have the idea thought out but it still moves all the files no matter what. Can someone help me out. Thanks

#!/bin/bash

for filea in *.*;
do

   tempa=$filea
   for fileb in `ls /test/ *.*`;
   do
     tempb=$fileb
     echo "tempb is now $tempb"
     echo $tempa | tr '[:upper:]' '[:lower:]'
    echo $tempb | tr '[:upper:]' '[:lower:]'
     if [  "$tempb" = "$tempa" ];
     then
        
        mv "$filea" "~/Desktop/test"
     fi
   done
done

---

### Post by raptor2552 on 2008-01-17
You need a white space when using brackets in the if statement:
if [ "$tempb" = "$tempa" ] #wrong
if [   "$tempb" = "$tempa"   ] #correct

---

### Post by lucient on 2008-01-17
aren't those two exactly the same?

---

### Post by dagnabit dang doohickey on 2008-01-18
You may want to give this script a try. The script will display all the files subject to imminent movage, but won't take any action without your confirmation. Test it on copies before committing it to use.

```

#!/usr/bin/env bash

## cfiles - move files that share a common name
##
## Usage: cfiles DIRECTORY_A DIRECTORY_B DESTINATION
##
## Description:
## This script will move all the files from DIRECTORY_B to DESTINATION
## that have a file name in common with a file in DIRECTORY_A.
## The script is not recursive and it will not move directories.

usage="Usage: `basename $0` DIRECTORY_A DIRECTORY_B DESTINATION"

if [ $# -lt 3 ] ; then
    echo "`basename $0`: insufficient number of arguments"
    echo $usage
    exit 1
elif [ $# -gt 3 ] ; then
    echo "`basename $0`: too many arguments"
    echo $usage
    exit 1
fi

for i in $* ; do
    if [ ! -d "$i" ] ; then
        echo "`basename $0`: $i: no such directory"
        exit 1
    fi
done

dir_a="$1"
dir_b="$2"
dir_c="$3"    # DESTINATION directory

comm -12 <(ls -p1 "$dir_a") <(ls -p1 "$dir_b") | grep -v /$ > /tmp/commlist

if [ -s /tmp/commlist ] ; then

    echo -e "\nThe following file names are common to both directories:\n"
    cat /tmp/commlist
    echo

    read -p "Do you want to move the duplicates from $dir_b to $dir_c? [y/N] " YesNo
    case $YesNo in
        y|Y) sed -e "s#.*#$dir_b\/&#" /tmp/commlist | xargs mv -t "$dir_c" && \
             echo -e "\nThe files have been moved.\n" ;;
        *) echo -e "\nNo files have been moved.\n" ;;
    esac

else
    echo -e "The directories do not contain any duplicate file names.\n"
fi

exit 0

```

---

### Post by lucient on 2008-01-18
Thanks for that script. But is there a way where i can ignore uppercase or lowercase when i can trying to create that commlist?

---

### Post by lucient on 2008-01-18
I found out how to do that but it seems that your move command isn't working

---

### Post by dagnabit dang doohickey on 2008-01-18
The following will perform a case insensitive comm:
```
comm -12 <(ls -p1 "$dir_a" | tr '[:upper:]' '[:lower:]') <(ls -p1 "$dir_b" | tr '[:upper:]' '[:lower:]') | grep -v /$ > /tmp/commlist
```

There will be problems with using the result of this, though. The resulting list will no longer match the file names of any files whose names have been translated.

---

### Post by lucient on 2008-01-18
Yea thats actually what i did and as you said not all the files were matched.  I was thinking if it would be better to use cmp to compare the two files and then only move them over.

---

### Post by dagnabit dang doohickey on 2008-01-18
I don't see how cmp would solve the problem, unless each directory were already exact duplicates of each other to begin with.
Something that comes to mind is using the resulting commlist with a case-insensitive find on DIRECTORY_B and executing a mv with find's -exec option.

---

### Post by lucient on 2008-01-18
But the commlist is an incomplete list because of the case sensitive files.

---

### Post by lucient on 2008-01-18
So i get that i need to do a case insensitive search on directory_a over directory_b to find the matching file names. But i do not know how i can do that in bash script using find. 

Would i have to take each file name in directory_a and then find it in directory_b?

---

### Post by dagnabit dang doohickey on 2008-01-18
Use this case-insensitive comm line (same as previously posted) for the commlist:
```
comm -12 <(ls -p1 "$dir_a" | tr '[:upper:]' '[:lower:]') <(ls -p1 "$dir_b" | tr '[:upper:]' '[:lower:]') | grep -v /$ > /tmp/commlist
```

Now, replace the mv line (the y|Y line) with this line which uses a case-insensitive find:
```
y|Y) xargs -a /tmp/commlist -I @ find "$dir_b" -maxdepth 1 -type f -iname "@" -exec mv -t "$dir_c" '{}' \;
```

Go ahead and give the script a whirl on some test directories.

---

### Post by lucient on 2008-01-18
I ran the script but the it did not find any duplicates at all. 
Also with the  code 

comm -12 <(ls -p1 "$dir_a" | tr '[:upper:]' '[:lower:]') <(ls -p1 "$dir_b" | tr '[:upper:]' '[:lower:]') | grep -v /$ > /tmp/commlist

It doesn't give the complete list of file names matching.
Say is Dir_A has Test.ps and test1.ps and Dir_B has test.ps and test1.ps, the commlist would only have test1.ps written.

---

### Post by dagnabit dang doohickey on 2008-01-18
I ran a bunch of tests and it's working fine on my end. This is the complete case-insensitive script:
```

#!/usr/bin/env bash

## icfiles - move files that share a case-insensitive common name
##
## Usage: icfiles DIRECTORY_A DIRECTORY_B DESTINATION
##
## Description:
## This script will move all the files from DIRECTORY_B to DESTINATION
## that have a file name in common with a file in DIRECTORY_A.
## The file name comparison is case-insensitive.
## The script is not recursive and it will not move directories.

usage="Usage: `basename $0` DIRECTORY_A DIRECTORY_B DESTINATION"

if [ $# -lt 3 ] ; then
    echo "`basename $0`: insufficient number of arguments"
    echo $usage
    exit 1
elif [ $# -gt 3 ] ; then
    echo "`basename $0`: too many arguments"
    echo $usage
    exit 1
fi

for i in $* ; do
    if [ ! -d "$i" ] ; then
        echo "`basename $0`: $i: no such directory"
        exit 1
    fi
done

dir_a="$1"
dir_b="$2"
dir_c="$3"    # DESTINATION directory

comm -12 <(ls -p1 "$dir_a" | tr '[:upper:]' '[:lower:]') <(ls -p1 "$dir_b" | tr '[:upper:]' '[:lower:]') | grep -v /$ > /tmp/commlist

if [ -s /tmp/commlist ] ; then

    echo -e "\nThe following file names are common to both directories:\n"
    cat /tmp/commlist
    echo

    read -p "Do you want to move the duplicates from $dir_b to $dir_c? [y/N] " YesNo
    case $YesNo in
        y|Y) xargs -a /tmp/commlist -I '%' find "$dir_b" -maxdepth 1 -type f -iname "%" -exec mv -t "$dir_c" '{}' \; && \
             echo -e "\nThe files have been moved.\n" ;;
        *) echo -e "\nNo files have been moved.\n" ;;
    esac

else
    echo -e "The directories do not contain any duplicate file names.\n"
fi

exit 0

```

---

### Post by bjornar on 2008-04-22
Hi
Thanks for a interesting script
I want to sort two folders with pictures.
I have one folder with raw files (.cr2) and one folder with the raw files converted to .jpg.
After screening of the jpg files I want to delete those raw files in the raw folder that does not have a corresponding jpg-file anymore.

My questions:
Can I use this script to do this?
How do I specify which folder(s) to screen? (dir_a,b and c).

Bjornar

---

### Post by dagnabit dang doohickey on 2008-04-26
This may do the trick for you, bjornar. The meat and potatoes of this new script is completely different than the other scripts in this thread. I tried modifying the previous script, but then came to the conclusion that it stinks and nobody should use it for nuthin'. :P
The problem with the previous script lies in the use of the comm command. It gives erratic results and it's a goofy way to deal with file manipulation.

This new script doesn't replace the old script, as it's function is completely different to handle bjornar's request. As always, test the script on copies before commiting it to use.

```

#!/usr/bin/env bash

## filebully - compare and move/delete files that do not share a common name
##             (with a user-definable extension handling)
##
## Usage: filebully DIRECTORY_A DIRECTORY_B [DESTINATION]
##
## Description:
## This script will move or delete all files from DIRECTORY_A that do not
## have a file name in common with a file in DIRECTORY_B. If DESTINATION is
## specified, the files will be moved, otherwise the files will be deleted.
## The file extensions of the compared files are user definable and may differ.
## The script is not recursive.

## Set file extension for DIRECTORY_A
## Single extension only
dir_a_ext="cr2"

## Set file extensions for DIRECTORY_B
## Multiple extensions ok
#dir_b_ext="jpg jpeg png tif tiff"
dir_b_ext="jpg jpeg png"

###############

usage="Usage: `basename $0` DIRECTORY_A DIRECTORY_B [DESTINATION]\nIf DESTINATION is not specified, files will be deleted instead of moved."

if [ $# -lt 2 ] ; then
    echo "`basename $0`: insufficient number of arguments"
    echo -e $usage
    exit 1
elif [ $# -gt 3 ] ; then
    echo "`basename $0`: too many arguments"
    echo -e $usage
    exit 1
fi

for i in $* ; do
    if [ ! -d "$i" ] ; then
        echo "`basename $0`: $i: no such directory"
        exit 1
    fi
done

dir_a="$1"
dir_b="$2"
if [ -n "$3" ] ; then
    dir_c="$3"    # DESTINATION directory
fi

fb_tmp="/tmp/filebully"
fb_can="candidate_list"
fb_act="action_list"
if [ -d "$fb_tmp" ] ; then
    rm -r "$fb_tmp"
fi
mkdir "$fb_tmp"

find "$dir_a" -maxdepth 1 -type f -iname "*\.$dir_a_ext" | sed -r "s#^.*/(.*)\$#\1#" | sort -di > "${fb_tmp}/${fb_can}"

if [ -f "${fb_tmp}/${fb_can}" ] ; then
	while read line ; do
		line_mod=`echo "$line" | sed -r "s#^(.*)\.${dir_a_ext}#\1#"`
		mate=0
		for extb in $dir_b_ext ; do
			if [ -f "${dir_b}/${line_mod}.${extb}" ] ; then
				mate=1
				break
			fi
		done
		if [ $mate -eq 0 ] ; then
			echo "$line" >> "${fb_tmp}/${fb_act}"
		fi
	done < "${fb_tmp}/${fb_can}"
fi

if [ -f "${fb_tmp}/${fb_act}" ] ; then
    echo -e "The following files in $dir_a have no corresponding file in $dir_b:\n"
    cat "${fb_tmp}/${fb_act}"
    echo
    if [ $# -eq 3 ] ; then
        read -p "Do you want to move these files from $dir_a to $dir_c? [y/N] " YesNo
        case $YesNo in
            y|Y) xargs -a "${fb_tmp}/${fb_act}" -I '{}' mv -v -t "$dir_c" "${dir_a}/{}" ;;
            *) echo -e "\nNo files have been moved.\n" ;;
        esac
    elif [ $# -eq 2 ] ; then
        read -p "Do you want to delete these files from $dir_a? [y/N] " YesNo
        case $YesNo in
            y|Y) xargs -a "${fb_tmp}/${fb_act}" -I '{}' rm -v "${dir_a}/{}" ;;
            *) echo -e "\nNo files have been deleted.\n" ;;
        esac
    fi
else
    echo -e "Each file in $dir_a has a corresponding file in $dir_b.\n"
fi

exit 0

```

---

### Post by bjornar on 2008-04-26
Hi again!
Thanks a lot for taking your time to looking in to my problem.
You really addressed my specific case here.
And what a good job you did, making understandable comments and structure.
Just a little bit too straightforward. You see, I'm new to bash scripting an d I want to understand whats going on. Have I understood you correctly in this part:

dir_a=/media/disk/pictures/test/cr2folder
dir_b=/media/disk/pictures/test/jpgfolder
if [ -n /media/disk/pictures/test/outputfolder ] ; then
    dir_c=/media/disk/pictures/test/outputfolder    # DESTINATION directory

replaces:

dir_a="$1"
dir_b="$2"
if [ -n "$3" ] ; then
    dir_c="$3"    # DESTINATION directory

And that's it?
What if I want to delete the excessive files?
Can I just leave it like this?;

dir_a=/media/disk/pictures/test/cr2folder
dir_b=/media/disk/pictures/test/jpgfolder
if [ -n "$3" ] ; then
    dir_c="$3"    # DESTINATION directory

---

### Post by dagnabit dang doohickey on 2008-04-26
Your understanding of the directories is correct.

Directory A: the directory to be modified. (location of your cr2 files)
Directory B: the comparison directory. (location of your jpg files)
Directory C: the optional destination directory where the files from directory A will be moved, if you would rather move them instead of deleting them.

You don't have to edit the script to specify any of these directories. Simply call the script with the directories as arguments.
Example usage assuming you saved the script as filebully:
```
filebully /media/disk/pictures/test/cr2folder /media/disk/pictures/test/jpgfolder /media/disk/pictures/test/outputfolder
```
If you would rather delete the files, instead of moving them, don't specify a destination:
```
filebully /media/disk/pictures/test/cr2folder /media/disk/pictures/test/jpgfolder
```


The only part of the script that you may possibly want to edit at some point is the following:
```
## Set file extension for DIRECTORY_A
## Single extension only
dir_a_ext="cr2"

## Set file extensions for DIRECTORY_B
## Multiple extensions ok
#dir_b_ext="jpg jpeg png tif tiff"
dir_b_ext="jpg jpeg png"
```

If you know that all the files in Directory B only have the extension .jpg (and not .jpeg or anything else), you can change ```
dir_b_ext="jpg jpeg png"
``` to ```
dir_b_ext="jpg"
```Depending on how many files you have, this may bring a noticeable speed improvement in the processing time.


Also, say, instead of cr2 files, you had a directory full of tif files that you wanted to remove undesired files from, you would change
```
dir_a_ext="cr2"
``` to ```
dir_a_ext="tif"
```


Or, maybe if someone was using this with sound files, they might change the settings to
```
dir_a_ext="aif"
dir_b_ext="mp3"
```

---

### Post by bjornar on 2008-04-27
Thanks a lot this will save me a lot of time.

I normally shoot raw images and I have not until now found a efficient post processing work flow. Now I can download my raw files (normally several hundred after a days shooting) from the camera, convert them to jpg with this script: [http://jcornuz.wordpress.com/2007/10/10/workflow-3-quick-raw-converting-batch/](http://jcornuz.wordpress.com/2007/10/10/workflow-3-quick-raw-converting-batch/)
, screen the keepers quickly (normally involving deleting at least half the jpegs). Then I can remove the .cr2 files I don't need to use storage space for, using this script.
So if you could help me with a screening script I'd be all set:)

Thanks again, I hope others will make use of this script as well.

---

