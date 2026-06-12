---
title: "(Help) Script to zip multiples folder in separate archives"
date: 2007-01-05
forum: General Help
---

### Post by Yuzem on 2007-01-05
I have a lot of folders, they are comic books and i whant to zip each folder to a different archive in one go.
I can't figure out how to do it.
I think it must be possible with a script.
Is it possible?
Anyone knows how to do it?

---

### Post by Jussi Kukkonen on 2007-01-05
```

#!/bin/bash
for i in $( ls ); do
  zip -r $i.zip $i
done
```

I didn't try this (so be careful), but it's probably very close to what you are looking for. 

The script is meant be run in the dir where the comic directories are and it  assumes all subdirs are comic dirs. You might want to add a path to *$i.zip* as the zips  currently  get created in the same directory.

---

### Post by Yuzem on 2007-01-05
Thanks for your answer.
I test it but it doesn't work.
The result is a zip file with the name of the script file an with the script inside.
Am I doing something wrong?

---

### Post by koenn on 2007-01-05
that means it works : the script zipped itself into a zipfile. 
Was the script the only file in the directory ?

---

### Post by Yuzem on 2007-01-05
No, I created some directories to test it but only the script was zipped.

---

### Post by Yuzem on 2007-01-05
I found out what was wrong, there were spaces in the directories names.
How can i fix it?

---

### Post by Jussi Kukkonen on 2007-01-05
ok, my bad -- just a moment...
```

#!/bin/bash
for i in $( ls ); do
  zip -r "$i.zip" "$i"
done
```

that ought to do it.

---

### Post by Yuzem on 2007-01-05
Yes, i tried that but it doesn't work.
I have the following dirs:
"/12 3"
"/1234"
"/12345"
"/123456"

Only the last 3 get zipped.

---

### Post by Jussi Kukkonen on 2007-01-05
```
for i in ./*; do 
  zip -r "$i.zip" "$i"; 
done

```

note to self: never underestimate the problems in shell script variable substitution... sigh. My stupidity really, going with the *ls* trick in the first place.

---

### Post by koenn on 2007-01-05
that's because the for ... in (list) uses space as a delimiter so the 12 3 directory is processed  as 2 separate directories : 12 and 3, the zip looks for a directory "12" and can't find it. 

Thats 1 reason I avoid folder names with spaces (and you'll see that in Linux, folder names can be quite long, but nearly never have spaces, but use _ and - or . instead/ 

If it's too much trouble to change the folder names, someone will have to come up with a more elaborate script to work around the spaces


edit - hm, someone already found a way ... nice. :-)

---

### Post by Yuzem on 2007-01-05
Perfect! That works.
Thanks a lot to both!

---

