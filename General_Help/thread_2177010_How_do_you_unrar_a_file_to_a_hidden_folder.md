---
title: "How do you unrar a file to a hidden folder"
date: 2013-09-26
forum: General Help
---

### Post by jacatone on 2013-09-26
I've been playing around with different themes and icons and notice when I try unraring a tar.gz file, Ubuntu won't let me add it directly into a .icons or .themes folder. I have to unrar them some place else then copy them into those hidden folders. Is there a way around this? Thanks.

---

### Post by rolltide101x on 2013-09-26
unrar e /home/user/1.rar /home/user/.themes

---

### Post by varunendra on 2013-09-26
> **jacatone said:**
> when I try unraring a **tar.gz** file, Ubuntu won't let me add it directly into a .icons or .themes folder...
I believe you can not use "**unrar**" to extract **.tar.gz** files. Use tar instead -

```
tar xzf archive.tar.gz -C <path to the hidden folder>/.themes/
```

---

