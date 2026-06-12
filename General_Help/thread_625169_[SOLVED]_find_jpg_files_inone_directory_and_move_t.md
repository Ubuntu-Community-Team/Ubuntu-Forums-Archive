---
title: "[SOLVED] find jpg files inone directory and move to another directory"
date: 2007-11-27
forum: General Help
---

### Post by werdna5225 on 2007-11-27
I have about 300 folders inside my /home/andrew directory.  In these 300 folders are some jpg images that I need, I would like to move them all(the images not the folders) to another folder, Is there any way to do this via command line?

---

### Post by PeterJS on 2007-11-27
Ok, the last version I had posted was missing a couple dollar signs. This one does work, I tested it using copy instead of move, but the commands work the same way so I'm confident the move version I posted here works.

```

#!/bin/bash

if [ -z $1 ]
then
    echo "Usage: $0 destination"
fi

JPGS=`find . -name "*.jpg" | grep -v "\./\."`

for FILE in $JPGS
do
    mv $FILE $1
done

```

---

### Post by enchance on 2007-11-28
It's more simple if you go to   /home/username/ and run the code below
```
$ find . -R "*.jpg" | mv '{}' /targetfolder/ \;
```
I suggest you test this first in a mock folder just to make sure.

---

### Post by PeterJS on 2007-11-28
I've seen the pipe and {} construct used a couple times in scripts, but I've never seen any documentation on it. What's the deal?

---

### Post by werdna5225 on 2007-11-28
cool... thanks guys

---

