---
title: "Copying a directory tree"
date: 2013-02-19
forum: General Help
---

### Post by ooleyguy on 2013-02-19
I want to be able to make a copy of the directories in one folder to another without copying the files that are in the original directory.

I do not want any files in the directories that are created. Just the empty directories.

There's a handy program I had in Windows that did it, but i can't find anything similar for linux/ubuntu

---

### Post by dino99 on 2013-02-19
here are a few ways to do it:

[http://stackoverflow.com/questions/11026859/make-copy-of-folder-tree-without-files](http://stackoverflow.com/questions/11026859/make-copy-of-folder-tree-without-files)

---

### Post by ooleyguy on 2013-02-19
Those all use DOS commands.

---

### Post by Vaphell on 2013-02-19
so you want to simply recreate the directory structure?

```
src='.'
dest='/some/dir'
while read -r d; do *echo* mkdir -p "$dest/${d#$src/}"; done < <( find "$src" -mindepth 1 -type d )
```
put proper directories in src and dest.
this will print the folders that should be created to see if they are ok. If you want to actually create them, remove *echo*.

---

### Post by steeldriver on 2013-02-19
I was just about to post something very similar - except it uses 'printf "%P"' to get the dir name with the sourcedir already removed

Without the 'mindepth 1' it will create the toplevel target dir if it does not already exist

```

while read -r -d $'\0' dir
do [ -d "$dir" ] || mkdir -pv "/path/to/targetdir/$dir"
done <  <(find /path/to/sourcedir -type d -printf "%P\0")

```

---

### Post by diesch on 2013-02-19
```
cd one_folder
find . -type d -exec mkdir -p "another_folder/{}" \;
```

---

### Post by sisco311 on 2013-02-19
Also check out BashFAQ 010 (link in my signature).

cpio is installed by default, so I'd probably use it.

Just for some fun, I added some basic error checks to my script:
```

#!/bin/bash

usage ()
{
    cat << EOF
usage:
    $0 SOURCE DEST

RETURN CODES:
    0    success
    1    missing source and/or destination directory
    2    too many options
    4    source not a directory
    8    destination not a directory

EOF
} >&2

errnodir ()
{
    cat << EOF
error: "$@": no such directory
EOF
} >&2

errnosod ()
{
    cat << EOF
error: you must specify a source and a destination directory
EOF
    usage
}

errtoomuch ()
{
    cat << EOF
error: too many arguments
EOF
    usage
} >&2


source="$1"
dest=$(readlink -f "$2")

if (( $# < 2 ))
then
     errnosod
     exit 1
fi

if (( $# > 2 ))
then
     errtoomuch
     exit 2
fi

if ! [ -d "$dest" ]
then
    errnodir "$dest"
    exit 8
fi

if cd "$source" > /dev/null 2>&1
then
    find . -type d -print0 | cpio -0pdumv "$dest"
else
    errnodir "$source"
    exit 4
fi

```

---

### Post by LewisTM on 2013-02-19
A single rsync command can do this:
```
rsync -av -f"+ */" -f"- *" Source/ Destination
```
The destination will be created if it does not exist. All directories contained in the source will be recursively copied inside the destination. Appending / to the source is important if you don't want the top dir to be copied inside the destination.

Cheers!

---

### Post by ooleyguy on 2013-02-20
Thank you all. I used sisco311's example and it worked smashingly. The only thing I had to do was rename the source and destination directories to remove the spaces in the directory names. It complained about having too many arguments.

---

