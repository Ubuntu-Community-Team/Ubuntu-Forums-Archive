---
title: "symbolic links into directory that doesnt exist"
date: 2007-09-28
forum: General Help
---

### Post by duncan.hawthorne on 2007-09-28
is there a way to force symbolic links to be made?

ie if i want to do
$ ln -s /etc/apt/sources.list ~/newdirectory/sources.list
but "new" doesnt exist, then it fails: "ln: creating symbolic link `/home/duncan/newdirectory/sources.list' to `/etc/apt/sources.list': No such file or directory"

is there a way to make the directory and put the symbolic link into it, all in one command

I would like to be able to do this for (perhaps) more difficult examples like
$ ln -s /etc/apt/sources.list ~/newdirectory/anothernewdirectory/sources.list 
all in one command.

any ideas?

thanks if you can help

---

### Post by kebes on 2007-09-28
You can use "mkdir -p" to create a sub-directory, and have it create all the parent directories, if required. So:
```
mkdir -p ~/newdirectory/anothernewdirectory
```
will work, even if "newdirectory" doesn't exist yet. So a two-step command to do what you want would be:
```
mkdir -p ~/newdirectory/anothernewdirectory
ln -s /etc/apt/sources.list ~/newdirectory/anothernewdirectory/sources.list 
```

If you really want it to be a single-step, you could write a bash shell script that takes the new directory path as an argument, and then performs both steps... Something like (save this to a file called "makequick.sh" or whatever, then do "chmod +x makequick.sh"):
```

#!/bin/bash

mkdir -p $1
ln -s /etc/apt/sources.list $1/sources.list

```
which you would then invoke like:
```
./makequick.sh ~/newdirectory/anothernewdirectory
```


Or, if you want a more general version:
```
#!/bin/bash

mkdir -p $1
ln -s $3 $1/$2

```
and you invoke:
```
./makequick.sh ~/newdirectory/anothernewdirectory sources.list /etc/apt/sources.list
```


Of course it depends how exactly you intend on using the command... Anyways, I hope that helps.

---

### Post by duncan.hawthorne on 2007-09-28
thanks thats really useful. ive learned a lot. ubuntuforums support is amazing

however, is there an easy way (ie a shell script) to split 

"~/newdirectory/anothernewdirectory/sources.list"
into 
"~/newdirectory/anothernewdirectory/" and "sources.list"

or even

"~/dir1/dir2/dir3/....../dir100/sources.list" 
into 
 "~/dir1/dir2/dir3/....../dir100/" and "sources.list"

so that it can be passed as 2 arguments to makequick. i want to seperate the bit after the last forward slash.

i want to make symlinks for lots of files so adding in a space isnt really efficient. i want to just have 
" ./makequick /etc/apt/sources.list ~/newdirectory/anothernewdirectory/sources.list "
instead of 
" ./makequick /etc/apt/sources.list ~/newdirectory/anothernewdirectory/ sources.list "

is this possible? thanks for helping

---

### Post by kebes on 2007-09-28
> **duncan.hawthorne said:**
> 
is there an easy way (ie a shell script) to split ... so that it can be passed as 2 arguments to makequick. i want to seperate the bit after the last forward slash.

i want to make symlinks for lots of files so adding in a space isnt really efficient. i want to just have 
" ./makequick /etc/apt/sources.list ~/newdirectory/anothernewdirectory/sources.list "
instead of 
" ./makequick /etc/apt/sources.list ~/newdirectory/anothernewdirectory/ sources.list "

is this possible? thanks for helping

If you're making a huge list of symlinks, it may be even easier to create a bash shell file (or a python file, or whatever) to make them all iteratively. The exact script would of course depend on what the symlinks you're trying to make are...


That having been said, here's a bash file that, as requested, automatically splits the argument so that you only have to pass it two arguments:
```

#!/bin/bash

PATHTOPARSE=$2

# Extract everything from the last slash.
# $2 is the second argument, which is passed to grep.
# grep uses a regular expression to extract the
# required piece. Specifically the expression "/[^/]*$"
# means "find a slash (/), followed by a sequence of many
# (*) characters that are not a slash ([^/]), which go
# until the end of the line ($)
FILENAME=`echo $PATHTOPARSE | grep -o "/[^/]*$"`


# Get the directory by stripping the filename from the path
DIRTOMAKE=${PATHTOPARSE%$FILENAME}

# Make directory
echo "Creating directory: "$DIRTOMAKE
mkdir -p $DIRTOMAKE

# Make symlink
echo "Making symlink $2 pointing to $1"
ln -s $1 $2

```

Which you can use like:
```

./makequick /etc/apt/sources.list ~/newdirectory/anothernewdirectory/sources.list

```
(Assuming I didn't make any mistakes!) I put some comments in the code to make it more readable. Pay attention to the use of backticks (not quotes!) on the line that sets the value of FILENAME (you may want to copy-and-paste to avoid typos).


I hope that does what you want. It's not the most elegant bash code, but I think it will work.

---

