---
title: "how to search for files inside archives"
date: 2007-06-17
forum: General Help
---

### Post by vadania on 2007-06-17
I have a collection of archived files (zip, jar). How do I find in which archive is the file I need? I have different search criteria: file name, creation date, file contents contains _something_, 

Do I have to manually open all archives and check out every single file, or is there a tool that does that for me?

---

### Post by s.deleeuw on 2007-06-17
I cannot completely answer your question, but this is how I search through a bunch of ZIP files (from the command line):

```
for FILE in *.zip; do
    unzip -t "$FILE" 2>&1 | grep "the_filename" >/dev/null && echo "$FILE";
done
```

---

### Post by zvacet on 2007-06-17
**places>search files**

or with this command if you know file name

```
whereis file_name
```

---

### Post by Nate53085 on 2007-06-17
tar -t will list all the files in a tar archive

unzip -l will list the files in a zip archive

so by doing :

tar -t | grep *filename*

    or

unzip -l | grep *filename*

you will be able to find a file in these types of archives

---

