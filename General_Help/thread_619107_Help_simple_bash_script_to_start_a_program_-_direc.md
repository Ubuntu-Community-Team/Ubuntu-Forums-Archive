---
title: "Help: simple bash script to start a program - directory."
date: 2007-11-21
forum: General Help
---

### Post by rytmisk on 2007-11-21
Hi

I am trying to start two programs in a row from a bash script. One is lying within another folder.

```
#! /bin/bash
#
# Starts mu server and then transana

python MessageServer/MessageServer.py &
python Transana.py
```

The thing is it doesn't work from a shortcut unless I provide a line with the exact path to the folder where the program is located. I'd rather have it portable so that the shortcut I will be making to this bash script locates the placement of the program (Transana.py - which is also the placement of the simple bash script).
I have tried to put a variety of "cd" commands, but none work. 

Anyone wants to help a total beginner?

Best regards
Ketil

---

### Post by el escocés on 2007-11-21
you can search for it then execute the search result.  

```
 find PATH -name Transana.py -exec '{}' ';' 
```where PATH is where the file should be '$HOME' '/' '.'

---

### Post by ihristov on 2008-04-23
I would suggest using find is not the best approach. It can take a long time and could potentially find a different file by the same name if you had 2.

A better way would be to do

```
# get the original file a link points to if it's a link
LINK_FILE=$(readlink -f "$0")

# determine the name of the directory where we ran from
if [ 0 = $? ]; then
	STARTUP_DIR=$(dirname "$LINK_FILE")
else
	STARTUP_DIR=$(dirname "$0")
fi

# at this point $STARTUP_DIR might be a relative path
cd "$STARTUP_DIR"

# retrieve the full path of the startup folder
STARTUP_DIR=$(pwd)
```

Now in the variable $STARTUP_DIR you will have the folder where your bash script is, so you can do something like:
```
python $STARTUP_DIR/MessageServer/MessageServer.py &
python $STARTUP_DIR/Transana.py
```

---

