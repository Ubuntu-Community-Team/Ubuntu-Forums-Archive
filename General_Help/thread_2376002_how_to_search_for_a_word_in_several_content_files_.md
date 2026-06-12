---
title: "how to search for a word in several content files at the same time"
date: 2017-10-29
forum: General Help
---

### Post by linux.girl on 2017-10-29
Hello friends,

I know how to search for filenames containing a certain word.

What I need is different - I need a command that searches for a word in a  directory that contains many files - but note - the word is not in the  title of the file, it is in the text.

Is there a way to find a command that scans the contents of all files in a directory searching for a specific word?

Thanks,

linux.girl

---

### Post by dragonfly41 on 2017-10-29
I use searchmonkey for that .. tick the box "containing" (text)
and use Expression Builder.

---

### Post by linux.girl on 2017-10-29
I only have cmd, no GUI. Any other suggestions?

---

### Post by jeremy31 on 2017-10-29
grep word directory
```
grep b43 /etc/modprobe.d/*
```
It will search every file in /etc/modprobe.d for b43 and actually list the filename containing the expression grep -e can also be used

---

### Post by slickymaster on 2017-10-29
Try```
grep -R "content_to_search" /path/to/directory
```

---

### Post by linux.girl on 2017-10-29
Thanks everyone, will mark as solved!

---

### Post by linux.girl on 2017-10-29
Wait, another question - what if I don't know in which directory is the file and I also don't know the filename? Could I do this word search with grep on all / ?

---

### Post by ajgreeny on 2017-10-29
In theory you could, but you will probably get many errors about files and folders that can not be read by you as user, and it may also take a very long time to run that depending on the size of your filesystem.

---

### Post by linux.girl on 2017-10-31
Many thanks for all the help!

---

