---
title: "Can I get a list of the file types stored on my hard drive?"
date: 2021-10-18
forum: General Help
---

### Post by sofasurfer on 2021-10-18
I don't want a listing of all files, I just want to know what file types are on my hard drive.

---

### Post by Impavidus on 2021-10-19
```
find / -type f -exec file -b {} \; | sort | uniq
```
find will list all files on your system, file -b will print file type. sort will sort them and uniq will make sure each type is listed only once. file may occasionally print a bit more than you want (like versions of the format or creation dates where this is stored in the file). Adding the -i option may help. Use the manuals for find, file, sort and uniq for more details.

---

### Post by sofasurfer on 2021-10-21
Thanks

---

