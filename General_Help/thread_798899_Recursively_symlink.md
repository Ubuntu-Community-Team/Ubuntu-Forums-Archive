---
title: "Recursively symlink"
date: 2008-05-18
forum: General Help
---

### Post by elwaywitvac on 2008-05-18
Anyone know how to:

1) copy a directory tree's structure so both root folders contain the same sub folders
2) Recursively symlink all the files in one tree to the other.

I know you could just symlink the root folders but in this case I'd like the users to be able to move the links around or delete links they don't want without modifying the original structure (read as one massive share allowing everyone to sort it their own way.)

Is there a way to do this with ln (which seems to have a -R option in all the man pages I've found but ubuntus..) or do I have to use a strange combination of cp/ln/find?

---

### Post by ibuclaw on 2008-05-18
I'll write one up for you quickly.
I've already (sort of) made a script similiar to this, only is actually copies everything, and not symlink it all.
But a quick mod on it should give you the result you want!

brb in about an hour...

Regards
Iain

---

### Post by ibuclaw on 2008-05-18
OK, here is my converted script (had to deflate it down a bit and remove lots of clutter).

```

#!/bin/bash
#####################################
#       Written by Iain Buc&#322;aw      #
# Under the GPLv3 Software Licensed #
#####################################

### Start ###
start-sync()
{
    echo "Starting Sync..."
    if [ -d "$1" ]
    then sync-dirs "$1" "$dest"
	 sync-syms "$1" "$dest"
    fi
}

sync-dirs()
{
    make-dir()
    {
	while [ $# -gt "0" ]
	do export dir=$(echo "${1##"$srcs"}")
	   mkdir -p "$dest""$dir"
	   shift
	done
    }
    
    srcs=$1
    dest=$2
    echo "Syncing Source Directories With Destination Folder..."
    srcs_dirs=$(find $srcs -type d)
    make-dir $srcs_dirs
}

sync-syms()
{
    sym-files()
    {
	while [ $# -gt "0" ]
	do export file=$(echo "${1##"$srcs"}")
           if [ $softsym -eq 1 ]
           then ln -s "$1" "$dest""$file"
           else cp "$1" "$dest""$file"
           fi
           shift
        done
    }
    
    srcs=$1
    dest=$2
    
    echo "Syncing Source Files With Destination Folder..."
    srcs_files=$(find $srcs -type f)
    sym-files $srcs_files
}

### Main Logic ###
if [ "$1" == "--soft" ] || [ "$1" == "-s" ]
then export softsym=1
     shift
else export softsym=0
fi

if [ ! "${1%%/*}" ]
then export srcs="$1"
else export srcs="$PWD"/"$1"
fi; shift
if [ ! "$1%%/*}" ]
then export dest="$1"
else export dest="$PWD"/"$1"
fi

start-sync $srcs

echo "Finished!"
echo "Exiting..."
exit 0
### End ###

```
Save the file as "symsync" or another.
Usage is:
[PHP]
# Create hard links from src to dest.
./symsync src dest
#Create soft links from src to dest.
./symsync -s src dest
# Create soft links from the path of source to dest.
./symsync -s /home/src dest
[/PHP]
It's pretty much straightforward.

Hard Links will take up more space, but your users cannot edit the original files if you hardlink them (it's the equivalent of copying).

Whereas Soft Links  will take up less space, but any edit in the soft link will change the original file too.

Tell us what you think of it, how the attempt at doing the job you wanted to get done either succeeded or failed.

And where I could touch up on improvements.

Regards
Iain

---

### Post by koenn on 2008-05-18
in bash :
```

#!/bin/bash

SRC="/home/koenn"
DEST="/home/copy"

mkdir -p $DEST 

## 1 - recreate SRC directory tree as DEST
find $SRC -type d |while read PATHNAME; do 
    mkdir -p "$DEST${PATHNAME#$SRC}" ; 
done

## 2 - create a a symlink under $DEST for each file under $SRC
find $SRC -type f |while read PATHNAME; do 
        NEW="$DEST${PATHNAME#$SRC}" ; 
        echo "$NEW" ; 
        ln -s "$PATHNAME" "$NEW" ; 
done 

```

---

### Post by elwaywitvac on 2008-05-18
Thanks koenn, the $x{y#z} is much cleaner than the sed syntax I was using of echo $y | sed "s%^$z%$x%"

I made some slight modifications so the final script I'm using is this:
```

src=$(cd $1 ; pwd)
dst=$(cd $2 ; pwd)

echo "Building new directories in $dest..."
for dir in $(find $src -type d); do
	mkdir -p "$dst${dir#$src}"
done

echo "Symlinking files..."
for src_f in $(find $src -type f); do
	dst_f="$dst${src_f#$src}"
	# don't overwrite files
	if [ ! -f dst_f ]; then
		ln -s $src_f $dst_f
	fi
done

echo "Success"

```

Also, tinivole, no offense but your script is kinda ugly with your disk usage instead of find.  You might want to try using one of these and replace ln with cp.

---

### Post by koenn on 2008-05-18
> **elwaywitvac said:**
> Thanks koenn, the $x{y#z} is much cleaner than the sed syntax I was using of echo $y | sed "s%^$z%$x%"

you're welcome.

I see you want to use positional parameters for src and dest; you could just do
src="$1"
dest="$2"

I see you prefer "for item in $(find ...)" over "find ... | while read ..."
I prefer the pipe because then the while loop starts as soon as find finds something, i.e. links already get created while find is still searching for more files. . I think with the for ... in $(find ...), find needs to be finished completely before the for-loop can start. Although in this case, that might be an advantage, because of the disk I/O going on.

---

### Post by ibuclaw on 2008-05-18
> **elwaywitvac said:**
> 
Also, tinivole, no offense but your script is kinda ugly with your disk usage instead of find.  You might want to try using one of these and replace ln with cp.

I wasn't aware of a "find" function.

Then again, I'm learning more about bash everyday.

And, yes, it does look a bit pear shaped at times.
But I suppose that is mainly to do with me prefering to do everything manually rather than letting other apps do my work for me (Old C habit, maybe I should of chosen another language as a starting point...)

[EDIT]
UPDATED!
Happy now? ;)

Hmm... Now you have a script that small, you might consider converting it to Perl, then you'll get more speed/efficiently out of it.

Regards
Iain

---

### Post by GoTTi74 on 2010-10-21
I really appreciate the script from koenn - thanks!
 
But now I have an additional need. While symlinking I need to change the file extension as well but as I'm new in bash - honestly - I don't have a clue how to make it... any help is appreciated ;-)
 
Thank you guys
 
GoTTi74

---

### Post by abhiatind on 2011-03-18
Doesnt the 'lndir' command do exactly that?

---

