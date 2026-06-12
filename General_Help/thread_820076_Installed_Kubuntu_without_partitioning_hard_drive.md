---
title: "Installed Kubuntu without partitioning hard drive"
date: 2008-06-05
forum: General Help
---

### Post by Dusk Eagle on 2008-06-05
Yes, I know, I'm an idiot, but I Installed Kubuntu without partitioning my hard drive. Is there any way I can recover any of the files that were deleted, specifically, my pictures? I've tried using "PC Inspector File Recovery" and "Restoration" with wine and that didn't work, but is there any other way of recovering those files? (I'm not currently using said computer in order to avoid overwriting those files).

---

### Post by rraj.be on 2008-06-05
try this link

```
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
```

PC inspector is the powerfull D/R soft i ever used n windows.

---

### Post by Dusk Eagle on 2008-06-22
**Problem Fixed, old version below.**

All right, so I went to the link above and decided to use photorec to get back my files. After doing that I Googled for a way to sort the recovered data and found this code: (Running from /home/username/) 
```

#!/bin/bash

if [ -z $1 ]
then
    echo "Usage: $0 destination"
fi

JPGS=`find . -name "*.jpg" | grep -v "\./\."`

for FILE in $JPGS
do
    mv $FILE $Pictures/
done

```

After running it, I got back a bunch of picture files, but they were all 10kb files from my Internet cache. What do I do differently to get back all my other jpg pictures?

---

