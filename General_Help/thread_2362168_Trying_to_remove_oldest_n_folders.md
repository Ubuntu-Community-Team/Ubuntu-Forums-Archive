---
title: "Trying to remove oldest n folders"
date: 2017-05-25
forum: General Help
---

### Post by davaweb on 2017-05-25
I'm trying to include this in a script so that all but the last 5 folders in a folder are deleted by modification date:

cd /<path-to-folder>
rm -rf 'ls -t -r | tail -n +6'

The results of the pipe
'ls -t -r | tail -n +6'
should be fed to
 rm -rf
as the folders to delete but nothing happens.

Help please :-)

---

### Post by sisco311 on 2017-05-25
Check out BashFAQ #3 (link in my signature).

If you need more help, please feel free to ask.

---

