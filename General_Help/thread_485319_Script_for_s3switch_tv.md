---
title: "Script for s3switch tv"
date: 2007-06-26
forum: General Help
---

### Post by jides82 on 2007-06-26
hi,

my laptop has a s3savage video card and I use the utility **s3switch **to switch from lcd to tv output.

I want to create an icon that make this switching...I thought about writing down a small script. I tried that (I followed some instructions from Ubuntu forum). Unfortunately I need to call **s3switch** with the **sudo** command ( I guess because it is install for root user only) and my password is required.

My question is, it is still possible to do such a script even if my password is required? If yes, how do you do that?

thanks.
:D

---

### Post by bodymind on 2007-07-05
you can use gksu after the command with su.. ;)

just like this:

```
gksu s3switch lcd
```

---

