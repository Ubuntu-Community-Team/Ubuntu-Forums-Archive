---
title: "Archive Script"
date: 2013-08-02
forum: General Help
---

### Post by trippinnik on 2013-08-02
I'm looking for a script that can take a series of folders that use a date label format, compress each in a gunzip and remove the existing folder.

ie


20120915
20120917
20121011
..

create
20120915.tar.gz

---

### Post by newbie-user on 2013-08-02
Verify that the archives are created correctly before adding the rm line. Try this:
```
#!/bin/bash

FOLDERS=$(ls /path/to/folders)

for i in $FOLDERS
     do
          tar -czf /path/to/archive/$i.tar.gz $i
     done

rm -rf /path/to/folders/$i

exit 0

```

---

