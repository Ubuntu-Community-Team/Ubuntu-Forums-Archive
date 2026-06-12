---
title: "Find Duplicate Images"
date: 2007-01-19
forum: General Help
---

### Post by OOzypal on 2007-01-19
One of the reason I switched to Linux is because of its power to do things better than Win and I am sure there a way in linux to do what I want.

Is there a program (command line) that will find duplicate images based on interal image data (binary chk)?

Will Imagemagick do it?

---

### Post by yota on 2007-01-19
Hi, 

the 'diff' command tells if two files (or directories) are the same or not, so it can be used for your purpose.
from 'man diff'
> 
 -s  --report-identical-files
              Report when two files are the same.

I think that the main problem comes in when you eventually want to automate a comparison between two image collections, but some (maybe non-trivial) scripting should be able to handle it.

Hope this helps!

---

### Post by lamego on 2007-01-19
Install the fdupes package and use "fdupes" on the terminal...

---

### Post by DarthPooky on 2008-07-07
if you want to search subdirs use > fdupes (dir to scan here) -r
edit: it might seem to hang but it isn't

---

