---
title: "Rename files so words fit onto eight chracter lines????"
date: 2008-07-01
forum: General Help
---

### Post by tatt on 2008-07-01
I have found some bulk renaming programs but are unable to do this....



I have many mp3 music files.

My mp3 player displays the file and folder names on its display which is eight characters long.

I want to bulk rename files so words fit properly onto each line of eight characters and if not add spaces so the word will be shown next instead of half of a word at the end of the display and then the second half of the word at the beginning of the next.

i.e

rename

James Blunt Goodbye my lover.mp3

to 

James **Blunt **Goodbye my lover.mp3

(stars are spaces) this forum removed the spaces on first post


I need to do this in bulk with folder names as well as filenames.

Is this possible???????????????/


Thanks in advance

Chris

---

### Post by unutbu on 2008-07-01
What if you have two files called
mattheson-song1.mp3
matthesooey-song1.mp3

How would you like these files renamed?

---

### Post by nick_h on 2008-07-01
You will have to write a script to do something like that.  If you write a script that renames a single file then you could run it using the find command as follows:
```
find /folder -type f -execdir rename.sh '{}' \;
```

There is a useful shell command called fold which may help.  For the manual page type:
```
man fold
```

To get you started the script might be something like:
```
#!/bin/bash
IN=`basename "$1"`
OUT=`echo "$IN" | fold -s -w8 | awk '{s = s substr($0 "       ",0,9)} END {print s}' -`
mv "$IN" "$OUT"
```

I don't think that it will do quite what you want though.  Be careful if you try to use it.  I suggest you make backups first.

---

### Post by tatt on 2008-07-02
Hi.

Any words longer than 8 just cut short at 7 and add a * or something maybe?

---

### Post by nick_h on 2008-07-02
> Any words longer than 8 just cut short at 7 and add a * or something maybe?
Yes, what you need to do is write a script that takes the filename as a parameter and then changes it to what you want.  Then the actual rename is easy.

I have quickly coded an example but you will need to test and debug it:
```
#!/bin/bash
IN=`basename "$1"`
OUT=`echo "$IN" | awk 'BEGIN {spaces = "        "}
    {for (i=1; i<=NF; i++) \ 
        if (length(line) + length($i) < 8) {
           line = line $i " "
        } else if (length(line) + length($i) == 8) {
           line = line $i
        } else {
           output = output line substr(spaces,0,9-length(line))
           if (length($i) == 8)
               line = $i
           else if (length($i) < 8)
               line = $i " "
           else
               line = substr($i,0,8) "*"
        }
	output = output line
    }
    END {print output}' -`
mv "$IN" "$OUT"
```

---

### Post by unutbu on 2008-07-02
Renaming your files may not be a good idea because one day you may regret changing the artists name just to make it 8 letters long. Here is a unix-y way around this problem: symlinks. The script below makes a copy of your music directory except in the duplicate directory, instead of actual files there are symlinks to your actual files. Symlinks are small files, so you won't waste much space. The name of the symlink has been modified so that the first and second words are 8 characters long. 

```

James Blunt Goodbye my lover.mp3   becomes   James   Blunt   Goodbye my lover.mp3 
mattheson artist song1.mp3         becomes   matthesoartist  song1.mp3
matthesooey artist song1.mp3       becomes   matthesoartist  song1-0.mp3

```

If your files are in a directory called music, then the script below will create a directory called music-0. When you want to play music, point the music player at the music-0 directory instead of the music directory.

Save this script in a file called '8char'
```

#!/usr/bin/python
# Usage: 
#   cd to the directory with the mp3 files. Run 8char.py in that directory. It will create a subdirectory called 8char, filled with renamed symlinks.
#   8char.py 

import os
import sys
import shutil
import re
pat=r'^\s*(?P<first>\S+)\s+(?P<middle>\S+)\s+(?P<last>.+)'
def uniquify(path):
        num=0
        newpath=path
        while os.path.isdir(newpath) or os.path.isfile(newpath):
                (pathpart,ext)=os.path.splitext(newpath)
                newpath=pathpart+'-'+str(num)+ext
                num+=1
        return newpath
                

cwd=os.path.normpath(sys.argv[1])
print "Processing %s"%cwd
if not os.path.isdir(cwd):
        print "%s is not a valid directory"%cwd
        exit
newcwd=cwd+'-0'
if not os.path.isdir(newcwd):
        print "Creating %s"%newcwd
        os.makedirs(newcwd)
else:
        print "%s already exists. Delete it first."%newcwd
        exit

for root, dirs, files in os.walk(cwd,False):
        newroot=root.replace(cwd,newcwd)
        if not os.path.isdir(newroot):
                os.makedirs(newroot)
        for name in files:
                filename=os.path.join(root, name)
                amatch=re.search(pat,name) 
                if amatch:
                        newfirst=amatch.group('first')[0:8].ljust(8)
                        newmiddle=amatch.group('middle')[0:8].ljust(8)
                        last=amatch.group('last')
                        newname=newfirst+newmiddle+last
                        newname=uniquify(os.path.join(newroot, newname))
                try:
                        os.symlink(filename,newname)
#			shutil.copy(filename,newname)
                except:
                        print "Failed to create symlink from %s to %s"%(filename,newname)
                        continue       

```

Make it executable:```

chmod 755 8char

```

If you have your files in a directory called 'music', then run it like this:
```

./8char ~/music

```

Edit: Ah yes, thanks nick_h, for your comment below. I forgot the OP wants this on an mp3 player. So, tatt, if you'd like to make a copy of all your files with the 8-character names, simply change 

```

                try:
                        os.symlink(filename,newname)
#			shutil.copy(filename,newname)

```

to

```

                try:
#                        os.symlink(filename,newname)
			shutil.copy(filename,newname)

```

If you want the script to rename the files in place instead of copying to another directory, post. I hesitate to write such a script because if I screw up you could lose files.

---

### Post by nick_h on 2008-07-02
> Renaming your files may not be a good idea because one day you may regret changing the artists name just to make it 8 letters long.
Yes, good point.  I was assuming that the OP was only going to rename the files on their mp3 player.  I would keep the original file format for the PC archive.  If the mp3 tags are set correctly it would be easy to rename them back though.

Using python may also be easier when the rules get more complex.

---

