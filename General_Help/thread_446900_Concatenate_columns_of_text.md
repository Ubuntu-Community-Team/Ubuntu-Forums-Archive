---
title: "Concatenate columns of text"
date: 2007-05-17
forum: General Help
---

### Post by Timtro on 2007-05-17
Hi all,

I have several (say 'm') text files, each with 'n' columns. I want to put them into a large single file with n*m columns.

Ideally, I would like to be able to take all m columns from the fist file, and then the right most m-1 columns from the remaining files (since the first column is the same in all of the files), but I'll take what I can get.

I've tried awk, cat, columns... and I'm convinced there is a simple way to do it, but I can't seem get get the right combination of commands. Can anyone help me out?

Thanks a million!

---

### Post by kebes on 2007-05-17
Well this is probably not the "simplest" way to do it, but a python script can import text files and sort the data the way you want it. For example:

```

#!/usr/bin/python

# Import libraries
import os
import array
import string

# This will temporarily hold all the data
# from the files
fulldataset = []

# List all files in the current directory
filesindir = os.listdir(os.getcwd())
# Warning: The ordering of the files is not
# really predicatble. If the columns are supposed
# to be ordered in a specific way, you will have
# to explicitly do a check on the order of the files.
# For example, to sort by filename, uncomment this:
# filesindir.sort()

for filename in filesindir:

    # Filter based on filenames
    if (filename[-4:]=='.txt'):
        fin = open(filename)
        filedata = fin.readlines()

        # Parse the text strings into data tokens
        filematrix = []
        for line in filedata:
            filematrix.append( line.split() )

        fulldataset.append(filematrix)


# The array fulldataset is now a matrix that contains
# (files, rows, columns)


# Build the data into a new array, organized
# as you need it
outputarray = []
irow = 0
for row in fulldataset[0]:
    fullrow = []
    # Using += will add elements onto the end of an array
    fullrow += fulldataset[0][irow]
    for file in fulldataset:
        # The indexing [1:] means "from the 2nd element onwards"...
        fullrow += file[irow][1:] 

    outputarray.append( fullrow )

    irow += 1


# Output the array as a string
outputstrings = []
fout = open("output.dat", "w")
for row in outputarray:
    print row
    # The spacer between data is a space, but could be anything:
    outputstrings.append( string.join(row, " " ) )
    fout.write( string.join(row, " " ) + "\n" )

fout.close()

```

To run it, save it in a text file, like "makecols.py" and then do:
```

chmod +x makecols.py

```
Then you can run it the usual way:
```

./makecols.py

```
(or just go: "python makecols.py")


I wrote the above code quickly. I think it runs fine and does what you want, but I certainly didn't optimize it or engineer it very well. Also, you will need to change it to suit your needs. Right now it imports all *.txt files and outputs a single file "output.dat". There are many ways you could modify or improve it...

Anyways, if you have any specific questions about the code, let me know...

---

### Post by Timtro on 2007-05-17
Wow, you went to so much trouble kebes!

Thank you so much! I've been wanting to learn python for a long time now, perhaps this is my in.

Thanks again!

---

### Post by kebes on 2007-05-17
No problem.

Python is a great language... I highly recommend it! (I'm sure this could all have been coded into a single line of awk, but, for me at least, it's faster to write a much longer and less efficient python script...)

Hope it works out for you.

---

### Post by stylishpants on 2007-05-17
You could also use "join".

```

fhanson@fhanson:/tmp$ cat file
a       1
b       3
c       5
d       7
fhanson@fhanson:/tmp$ cat file1
a       2
b       4
c       6
d       8
fhanson@fhanson:/tmp$ join file file1
a 1 2
b 3 4
c 5 6
d 7 8

```

Slightly trickier for >2 files, but still not hard:

```
fhanson@fhanson:/tmp$ cat file2
a       12
b       14
c       16
d       18
fhanson@fhanson:/tmp$ join file file1 | join - file2
a 1 2 12
b 3 4 14
c 5 6 16
d 7 8 18

fhanson@fhanson:/tmp$ cat file3
a       -2
b       -4
c       -6
d       -8
fhanson@fhanson:/tmp$ join file file1 | join - file2 | join - file3
a 1 2 12 -2
b 3 4 14 -4
c 5 6 16 -6
d 7 8 18 -8


```

---

### Post by Timtro on 2007-05-18
Thanks kebes, I have a feeling I'm going to find python quite useful.

stylishpants: awesome! Thanks! This definitely suits my needs, and you explained it very clearly.

Thank you both for spending so much time on your posts.

Cheers gentlemen,


Tim.

---

### Post by Timtro on 2007-05-23
Since I had a lot of files, I needed to script this. The join command works famously.

For anyone who may have this issue in the future, here is a simple script that will take all files with .dos extension and join them. Of course this behaviour is easily customized.

```

#!/bin/bash

JOINCOMMAND="join `ls *.dos | column -c 1 | head -n1 | tail -n1` `ls *.dos | column -c 1 | head -n2 | tail -n1`"

#echo "Starting with '"$JOINCOMMAND"'"

COUNTER=0

for FILE in *.dos; do
    let COUNTER=COUNTER+1
done

let COUNTER=COUNTER-2

for FILE in `ls *.dos | column -c 1 | tail -n$COUNTER` ; do
    JOINCOMMAND=$JOINCOMMAND" | join - $FILE" 
done

echo $JOINCOMMAND

$JOINCOMMAND

```

P.S

Sorry for the lack of commenting. The general idea of the script is to get  get a list of all of the .dos files and go through it one item at a time using the head and tail commands. As we go through the list of .dos files, we build a large set of pipes with the join command. That is, continually join and pipe that output into another join, and so on.

---

