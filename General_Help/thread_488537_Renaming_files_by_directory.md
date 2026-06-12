---
title: "Renaming files by directory"
date: 2007-06-30
forum: General Help
---

### Post by adam_kimber on 2007-06-30
I have sorted my Digital Camera files in folders, however I am looking for a way to rename files that grabs the folder name and then renames the files within that folder to the folder name plus a numerically ascending number. I want to then move them to a new folder. The object of the exercise is to make browsing the pictures easier. As I don't have to keep going up and down directories to view three images. 

File re-structuring would be something like this:

~/Pix/London/PICT01.jpg --> ~/Pix/London/London01.jpg --> ~/Newpix/London01.jpg
~/Pix/London/PICT02.jpg --> ~/Pix/London/London02.jpg --> ~/Newpix/London02.jpg
~/Pix/London/PICT03.jpg --> ~/Pix/London/London03.jpg --> ~/Newpix/London03.jpg
~/Pix/Paris/PICT04.jpg --> ~/Pix/Paris/Paris01.jpg --> ~/Newpix/Paris01.jpg
~/Pix/Paris/PICT05.jpg --> ~/Pix/Paris/Paris02.jpg --> ~/Newpix/Paris02.jpg
~/Pix/Paris/PICT06.jpg --> ~/Pix/Paris/Paris03.jpg --> ~/Newpix/Paris03.jpg

So the final directory Newpix has a images grouped by name like this 

London01.jpg
London02.jpg
London03.jpg
Paris01.jpg
Paris02.jpg
Paris03.jpg

I expect this could be do with some complex Bash scripting. Maybe a modifcation of this commnd > for i in $(find . -type f); do mv $i . ; done.

However none of the "Bulk rename" programs out there seem to do renaming by containing folder. 

Can anyone suggest any methods for achieving the above? I would like to set the program/script running and then come back when finished.

---

### Post by PaulFr on 2007-06-30
One way to accomplish this: create a file in your home directory called movefile with the following contents:```
#!/bin/bash

if test $# -ne 1; then
    echo "Wrong number of arguments"
    exit 1
fi
place=`echo $1|sed -e 's,/[^/]*$,,'|sed -e 's,.*/,,'`
pict=`echo $1|sed -e 's,.*/PICT,,'`
outf="$HOME/NewPix/${place}${pict}"
if test -f "$outf"; then
    echo "${place}${pict} already exists in output directory ! skipping"
    exit 1
fi
mv $1 $outf
echo "Moved $1 to $outf"
exit 0
``` then execute the following commands:```
chmod +x $HOME/movefile
find Pix -type f -name "PICT*.jpg" -exec $HOME/movefile "{}" \; > ~/move.log 2>&1
```When this is done, you can review move.log.
Of course, this is just one simple way, instead of all the 'sed' commands, you can use awk or basename/dirname if you are more comfortable with those tools.

---

### Post by adam_kimber on 2007-06-30
Hey. Thanks! That was a really useful script. I appreciate the time. I now need to swat up on what the sed commands are actually doing.

---

