---
title: "Using zip, what is the command to..."
date: 2024-08-30
forum: General Help
---

### Post by wyattwhiteeagle on 2024-08-30
Using zip, what is the command to compress multiple folders in one single directory to multiple zip files into a separate directory?

---

### Post by currentshaft on 2024-08-30
for f in $(find . -type d) ; do
n=$(basename $f)
zip -r /tmp/$n.zip $n
done

---

### Post by wyattwhiteeagle on 2024-09-01
> **currentshaft said:**
> for f in $(find . -type d) ; do
n=$(basename $f)
zip -r /tmp/$n.zip $n
done
Thanks but that didn't have the desired result.
I would still like to know for in-future.

What happened was that when I ran that command, it listed each folder with "(deflating)".
When I checked the result, there were no compressed items in the expected location.
That's not the desired result.

I ended up deleting the unwanted files, then using the system-provided GUI to archive each folder.

---

