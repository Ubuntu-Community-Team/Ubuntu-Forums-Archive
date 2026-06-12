---
title: "Did this comand copy the entire disk?"
date: 2007-12-28
forum: General Help
---

### Post by tuproxy on 2007-12-28
I wanted to copy an entire drive from one 500GB drive to another.  

I was in the mounted folder that had everything I wanted to copy.  Here is the command that I used:

```
# sudo cp -Rfv * /media/500-3/
```

should I have used
```
# sudo cp -Rafv * /media/500-3/
```?

---

### Post by p_quarles on 2007-12-28
The -a option would preserve links, so would be closer to an exact clone of the source drive. Other than that, the command you used copied everything.

---

### Post by geirha on 2007-12-28
Maybe. The * wildcard doesn't expand to hidden files and folders, so the hidden files and folders in the directory you ran the command from, would not have been copied (hidden files and folders in any subdirectories would be copied though)

I would have used ```
cp -av . /media/500-3
```

---

