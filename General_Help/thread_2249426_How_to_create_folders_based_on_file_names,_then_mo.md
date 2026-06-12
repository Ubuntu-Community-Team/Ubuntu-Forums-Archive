---
title: "How to create folders based on file names, then move the files into the new folders?"
date: 2014-10-22
forum: General Help
---

### Post by ambient007 on 2014-10-22
I have a bunch of video files all in one folder that I want to each be in it's folder that is named the same as the original file.

Example:

I have TOP (folder) which contains PENGUIN.MKV (file).

I want it to be TOP (folder) containing PENGUIN (folder) containing PENGUIN.MKV (file).

TOP (folder) also contains about 50 other files, which each need their own folder.



How can I do this without manually creating, renaming and then moving each one individually?


I've been using Ubuntu for a while, but don't know much (anything) about the terminal or scripting.

I could do it by hand I guess, but I'd rather learn how to not have to. Thanks!

---

### Post by Vaphell on 2014-10-22
```
for f in *.*; do d=${f%.*}; mkdir "$d"; mv "$f" "$d/$f"; done
```

---

### Post by ambient007 on 2014-10-22
> **Vaphell said:**
> ```
for f in *.*; do d=${f%.*}; mkdir "$d"; mv "$f" "$d/$f"; done
```

Can someone break this down for me? I don't really know anything about the terminal (I assume this is a terminal command?), but would like to learn rather than just copy/pasting. 

I'm not too sure what to do with this, I assume some of those need to be replace with the files/location but I wouldn't know how.


Vaphell, thanks for taking the time to help me out.

---

### Post by Vaphell on 2014-10-22
```
for f in *.*         # for each file $f maching the *.* pattern
do
    d=${f%.*}        # $d = filename $f with extension (.*) stripped (%)
    mkdir "$d"       # make-dir $d
    mv "$f" "$d/$f"  # rename/move $f to $d/$f
done
```

---

