---
title: "Moving all of a kind of file to a single folder"
date: 2013-02-10
forum: General Help
---

### Post by cinematography on 2013-02-10
I used to have the bad habit of making too many subfolders. I'm trying to correct this mistake by moving more of my files closer to the root directory.

On one drive I have .txt files scattered all over the place, and I was wondering if there was a way to recursively locate all of these files and move them to a single folder using the command Terminal.

Your help would be appreciated.

---

### Post by cthugha on 2013-02-10
mv `find -type f -name "*.txt"` /path/to/directory 
should do it

this will find every file with the .txt extension in the working directory or a child directory of the working directory and move it to /path/to/directory

---

### Post by schragge on 2013-02-10
The advice above works fine if none of your files contains spaces or other unusual characters in its name. Otherwise, try
```

find -type f -name \*.txt -exec mv -t /path/to/directory -- {} +

```

---

### Post by cinematography on 2013-02-10
This forum is the best. 

Thank you both very very much.

---

