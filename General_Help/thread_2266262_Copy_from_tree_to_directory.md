---
title: "Copy from tree to directory"
date: 2015-02-21
forum: General Help
---

### Post by CkDGTAT on 2015-02-21
Hi,

Suppose I have files located at random places

```
~/a1/a2/file
~/a3/file2
...
```

How can I have those files copied in one directory in a single cmd?

---

### Post by TheFu on 2015-02-21
if you can create a list of those files, either with a list or using a command like **find**, then you can merge all the "source" onto a single line with a single "target" and use **mv**.

```
mv ~/a1/a2/file ~/a3/file2 ~/a3/file3 ... /tmp/file100 /place/I/want/all/of/these/files/
```
If there is a pattern, then using find might be easier.
```
find ~/a* -type f -iname \*.mp4 -exec mv {} /place/I/want/all/of/these/files/ \;
```

There is an issue - if the filenames are not unique, only the last one in the list will remain in the target directory. If that is the case for you, there are solutions, but they are a little more complex.

Oops - you wanted to cp files.  Use cp instead of mv in the examples above.

---

### Post by Holger_Gehrke on 2015-02-21
Just use 'cp' in a shell. If the last argument is a directory, all arguments before the last will get copied to it.

Example:
```

cp /usr/share/doc/python-setuptools/using /usr/share/doc/diveintopython/examples/autosize.py /usr/share/doc/gimp/NEWS.gz .

```
will copy the listed files into the current working directory.

---

