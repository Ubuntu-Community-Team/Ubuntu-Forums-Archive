---
title: "Bash help"
date: 2020-06-06
forum: General Help
---

### Post by raleigh3 on 2020-06-06
This is not working. 

I get

andy@7_~$ BkupCookies.sh
cp: cannot create regular file '/SDB1_Mountpoint/Ubuntu_Mate_18.04//home/andy/.mozilla/firefox/9r99csdk.default/_06_06_2020.cookies.sqlite': No such file or directory

It might have to do with the 2 // after 18.04.

#!/bin/bash
# 
#----------------------------------------------------------------------------
# 
# this is FF profile directory /home/andy/.mozilla/firefox/9r99csdk.default/
## Get current date ##
_now=$(date +"%m_%d_%Y")
 
## Appending a current date from a $_now to a filename stored in $_file ##
_file="/home/andy/.mozilla/firefox/9r99csdk.default/_$_now.cookies.sqlite"
 
cp /home/andy/.mozilla/firefox/9r99csdk.default/cookies.sqlite /SDB1_Mountpoint/Ubuntu_Mate_18.04/"$_file"

---

### Post by TheFu on 2020-06-06
don't use leading underscores for bash variables.
check the substitutions where there are excess '$'  and '_' characters that don't make sense.
check that ' match and " match
run the program with -x bash option.

---

### Post by TheFu on 2020-06-06
whenever posting shell commands and output, please, please use code tags.

---

### Post by Holger_Gehrke on 2020-06-06
A small quote from 'man bash':
> name:   A word consisting only of alphanumeric characters and underscores, and beginning with an alphabetic character or an underscore.  Also referred to as an identifier.
So while variable names starting with an underscore are unusual and IMHO ugly, they are legal.

The problem is quite simple: 'cp' does not create directories (with the exception of recursive copies, but then you're copying a directory and **all** it's contents including the directories ...). So if '/SDB1_Mountpoint/Ubuntu_Mate_18.04/home/andy/.mozilla/firefox/9r99csdk.default/' does not already exist it won't be created and the copy will fail. You could run 'mkdir -p $(dirname /SDB1_Mountpoint/Ubuntu_Mate_18.04/$_file)' before the 'cp'; 'dirname' cuts off the last component of a path, normally a filename and does not need the file or the directories to exist and 'mkdir -p' will create all the non-existing directories along the given path in one command.

Holger

---

### Post by TheFu on 2020-06-06
i saw at least 3 typos in the script.  The use of underscores appears to be an issue in at least 1 part of the script.  Just because something is possible, that doesn't make it a smart idea.   Details matter as my post above points out with a list of problems.

But me pointing out each exact issue won't be "teaching to fish."

---

### Post by raleigh3 on 2020-06-06
I will restate my desire.

I would like to copy a file to another directory but with the date embedded within that file name.

Ex. cookies.sqlite -> 6_6_20.cookies.sqlite

---

### Post by norobro on 2020-06-06
Try this:```
$ cp [COLOR=#000000]cookies.sqlite[/COLOR] $(date +"%m_%d_%Y").[COLOR=#000000]cookies.sqlite[/COLOR]
```> **raleigh3 said:**
> ... It might have to do with the 2 // after 18.04. Bash ignores consecutive slashes. You can test by executing the following:```
$ cd /home/andy/////.mozilla
```

---

### Post by lvm on 2020-06-07
Does the path '/SDB1_Mountpoint/Ubuntu_Mate_18.04//home/andy/.mozilla/firefox/9r99csdk.default/' exist? Looks like it doesn't, and cp cannot create folders as needed, you should use " mkdir -p "`dirname "/SDB1_Mountpoint/Ubuntu_Mate_18.04/$_file"`" && cp .... " or rsync to copy files while creating all necessary folders. Contrary to what is said aboveunderscores are allowed in bash variables anywhere, multiple slashes are pruned automatically and excessive use of code tags is annoying and should be reserved for cases when using fixed font to preserve vertical alignment is important.

---

### Post by TheFu on 2020-06-07
I remember seeing mismatched '" stuff.  Must have been my old eyesight.  There is an extra '_' in there still.

I'd not have a script for just 1 file, but ... 
```
#!/bin/bash -x

if [ -z $1 ] ; then
   echo  "A full path to the input file is required, 
        Usage:  $0 /path/to/file"
   exit 1
fi
SRC_FILE="${1:-/dev/stdin}"
TGT_DIR="/SDB1_Mountpoint/Ubuntu_Mate_18.04"

SRC_DIR=$(dirname $SRC_FILE)
FILENAME=$(basename $SRC_FILE)
TODAY=$(date +"%F")
/bin/cp   "$SRC_FILE"  "$TGT_DIR/$TODAY-$FILENAME"

```

This will result in a file copy into /SDB1_Mountpoint/Ubuntu_Mate_18.04/yyyy-mm-dd-filename.  No extra subdirs. If you want to mirror a directory, I'd use rsync and mkdir backup "set" directories with a yyyy-mm-dd at a   the /SDB1_Mountpoint/Ubuntu_Mate_18.04/yyyy-mm-dd/ level.

If I wanted a backup, I'd use rdiff-backup and let it handle the versioning, diffs, in an efficient way.

---

### Post by raleigh3 on 2020-06-08
This works.

> cd /home/andy/.mozilla/firefox/9r99csdk.default/
cp cookies.sqlite $(date +"%m_%d_%Y").cookies.sqlite
mv *.cookies.sqlite /home/andy/Maxtor_Backups/


Thanks to all for your help and patience. :-)

---

### Post by raleigh3 on 2020-06-08
This works.

> cd /home/andy/.mozilla/firefox/9r99csdk.default/
cp cookies.sqlite $(date +"%m_%d_%Y").cookies.sqlite

But how can I move it to another directory because the name will always be different?

---

### Post by norobro on 2020-06-08
As others have pointed out the problem with your original script was the destination path **not** the file name. That script should work if the path that you are copying to exists and is writable. @Foo's solution in post #10 will work with the correct paths also.


That being said, a brute force copy from the command line would be:```
cp /path/to/cookies.sqlite /some/other/path/$(date +"%m_%d_%Y").cookies.sqlite
```

---

### Post by ActionParsnip on 2020-06-08
What is the reason for the copy anyway? What are you actually trying to achieve?

---

