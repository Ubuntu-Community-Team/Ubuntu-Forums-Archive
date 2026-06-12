---
title: "unrar - recursing directories"
date: 2008-03-09
forum: General Help
---

### Post by OoooMatron on 2008-03-09
Does anyone have a little script to enable me to unrar stuff and recurse through a list of directories unraring whatever is in there?

---

### Post by ghostdog74 on 2008-03-09
very simplistically
```
find /path -name "*.rar" -exec unrar e "{}" \;

```

---

### Post by RSLxH on 2008-03-09
> **OoooMatron said:**
> Does anyone have a little script to enable me to unrar stuff and recurse through a list of directories unraring whatever is in there?

Lol! That sounds like one of those downloaded movies that is split into about 30 rar files...... er.... that I was told about once...... by a bloke in a pub. 
Never download anything like that my self. ;)

---

### Post by OoooMatron on 2008-03-09
Lol, actually that's not what it is, since multiarchives will extract just by unraring any one of the files.

It sounds more like when you've got a batch of them in different folders and are too lazy too right click and extract. So that bloke told me ;)

Thanks for the tip ^!! I will try it out!

---

