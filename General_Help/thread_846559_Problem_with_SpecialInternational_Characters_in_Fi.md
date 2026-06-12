---
title: "Problem with Special/International Characters in Filenames"
date: 2008-07-01
forum: General Help
---

### Post by gib2800 on 2008-07-01
Hello, 
  I am having problems in Kubuntu 8.04 copying files and folders with international or special characters in their name (à, ö, ç, ñ, etc). Copying any other files works fine, but ones with special characters in the filename results in this error "Could not write to /location/file.ext". It sometimes gives me the option to skip that file, meaning it will copy non-special character files only. Other times there is no message but the files are not copied. It doesn't matter what the extension is. The only way I can copy these files is to rename them without the special characters, which is tedious for all of my music files which I am backing up. 
Does anyone know of a solution?

Update: I noticed that this is only a problem between an internal ntfs partition and an external ntfs-3g hard drives when using Kubuntu. It has in the past worked using XP to backup data from the same internal partition to the same external drive.

---

### Post by ilrudie on 2008-07-02
> **gib2800 said:**
> Hello, 
  I am having problems in Kubuntu 8.04 copying files and folders with international or special characters in their name (à, ö, ç, ñ, etc). Copying any other files works fine, but ones with special characters in the filename results in this error "Could not write to /location/file.ext". It sometimes gives me the option to skip that file, meaning it will copy non-special character files only. Other times there is no message but the files are not copied. It doesn't matter what the extension is. The only way I can copy these files is to rename them without the special characters, which is tedious for all of my music files which I am backing up. 
Does anyone know of a solution?

Update: I noticed that this is only a problem between an internal ntfs partition and an external ntfs-3g hard drives when using Kubuntu. It has in the past worked using XP to backup data from the same internal partition to the same external drive.

Using 
```
ls -li
```will let you see the inode numbers.

Then
```
find -indode <inodenum> -exec mv {} <path to destination> \;
``` should allow you to move files by inode rather than by name so it doesn't matter what the file is called.

---

### Post by ghostdog74 on 2008-07-02
unless i miss it, specifying wildcard along with other characters (not special characters) might also work. Have a try.

---

### Post by beneedict on 2008-07-10
I do have the same problem, but I have too many files to rename all of them. is there no other workaround for external harddrives?

THX, Benedikt

---

### Post by greyblitz on 2008-11-12
Has anyone come up with a solution for this? I'm having the same problem too and I don't think doing each one individually is going to be very efficient. Thanks very much

---

### Post by ilrudie on 2008-11-12
This script should be a good starting point to do a mass rename.  What it does is rename [COLOR=Red]_**everything in the current working directory**_[/COLOR] to its inode number.  This does include directories but does not include hidden files.  Because I'm not really sure what your end goal is or how you want these files renamed its hard to make the script more specific.  If this doesn't meet your needs and you can't figure out how to modify it post back with more information on how you want it to work and I can help you get something you like.

Hope this helps.  Remember not to use it on directories that contain things you don't want renamed.
```

#!/usr/bin/ksh

CURDIR=`pwd`
echo This will rename ALL the files in $CURDIR to their inode number
echo Do you want to continue? [y/N]
read CONTINUE
if [[ $CONTINUE = y ]]
then
echo continuing...
set -A INDOES
INDOES=`ls -li | grep -v total | awk '{printf("%s\n",$1)}'`
for CURINODE in $INDOES
do
        echo current inode: $CURINODE
        find $CURDIR -inum $CURINODE -exec mv {} $CURINODE \;
done
else
echo exiting...
fi

```

I don't recall if ksh is installed by default under Ubuntu or not but this script uses ksh.  If its not installed just run 'sudo apt-get install ksh'.  I'm not sure if this script will work with bash or not so I'd recommend installing ksh.

---

### Post by D0nJ0seph on 2011-10-25
> **ilrudie said:**
> This script should be a good starting point to do a mass rename.  What it does is rename [COLOR=Red]_**everything in the current working directory**_[/COLOR] to its inode number.  This does include directories but does not include hidden files.  Because I'm not really sure what your end goal is or how you want these files renamed its hard to make the script more specific.  If this doesn't meet your needs and you can't figure out how to modify it post back with more information on how you want it to work and I can help you get something you like.

Hope this helps.  Remember not to use it on directories that contain things you don't want renamed.
```

#!/usr/bin/ksh

CURDIR=`pwd`
echo This will rename ALL the files in $CURDIR to their inode number
echo Do you want to continue? [y/N]
read CONTINUE
if [[ $CONTINUE = y ]]
then
echo continuing...
set -A INDOES
INDOES=`ls -li | grep -v total | awk '{printf("%s\n",$1)}'`
for CURINODE in $INDOES
do
        echo current inode: $CURINODE
        find $CURDIR -inum $CURINODE -exec mv {} $CURINODE \;
done
else
echo exiting...
fi

```

I don't recall if ksh is installed by default under Ubuntu or not but this script uses ksh.  If its not installed just run 'sudo apt-get install ksh'.  I'm not sure if this script will work with bash or not so I'd recommend installing ksh.

i'm new in kubuntu so idk how to run this script in the directory i want... Should i only replace "pwd" for the directory location?

---

