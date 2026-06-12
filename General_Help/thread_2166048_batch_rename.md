---
title: "batch rename"
date: 2013-08-07
forum: General Help
---

### Post by gychang on 2013-08-07
I have files with a space in name that I need to get rid of and need to know command.

e.g.  I have 2 files:  A 1.txt and A 2.txt and I want to end up with A1.txt and A2.txt

what is the proper command to accomplish in batch fashion?

thanks in advance.

---

### Post by The Cog on 2013-08-07
```
rename 's/ //' *
```
should do the trick. Rename by substituting space with nothing on all files.

---

### Post by gychang on 2013-08-07
> **The Cog said:**
> ```
rename 's/ //' *
```
should do the trick. Rename by substituting space with nothing on all files.

that works well, thanks, have another question.  Now I want to batch change A1.txt and A2.txt to 1.txt and 2.txt.  What is the command that is needed?  

I want to thank you, by knowing above command it saved me lots of time already.

---

### Post by Lars Noodén on 2013-08-07
The same program (rename) will do the trick there, too.   But you will need to change the regular expression being searched and replaced (s///).  rename has a dry run option (-n) so if you run rename with -n it won't actually change anything and you are safe to try to find the pattern that works for you.  Once it is shown to be working, take away -n and let it make the changes.

It is the s/// that is key.  It works like s/find/replace/

---

### Post by The Cog on 2013-08-08
```
rename -n 's/A([0-9]+\.txt)/$1/' *
```
Don't you just ***love*** regular expressions?

---

