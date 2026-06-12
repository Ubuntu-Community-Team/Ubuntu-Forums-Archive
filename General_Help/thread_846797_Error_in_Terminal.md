---
title: "Error in Terminal??"
date: 2008-07-01
forum: General Help
---

### Post by cheruvim on 2008-07-01
So my friend has a folder whose name starts with '-=' so to find out what's in it I do the following:

```
ls -l -- -=*
```

and get the content list.

Then I do 
```
sudo chgrp -R * somegroup
```

and get the following:

```

chgrp: invalid option -- =
Try `chgrp --help' for more information.
```

Now how did that argument get passed to that command???? There must be something about the Terminal and that option that I'm missing...

:confused:

C.

---

### Post by cheruvim on 2008-07-01
OMFG I think I just figured it out... 

It's the wildcard! The shell doesn't like dashes...

---

### Post by g2g591 on 2008-07-01
actually an easier way to do the ls command is "ls -l \-\=" . the \ tells it to consider teh next character as part of (or in this case, the whole) name.This works for every cli command.  so, do sudo chgrp -R \-\= somegroup.
EDIT:oops , missed a tiny bit of your message, the - being infront of = .

---

### Post by cheruvim on 2008-07-02
> **g2g591 said:**
> actually an easier way to do the ls command is "ls -l \-\=" . the \ tells it to consider teh next character as part of (or in this case, the whole) name.This works for every cli command.  so, do sudo chgrp -R \-\= somegroup.
EDIT:oops , missed a tiny bit of your message, the - being infront of = .

I find it doesn't work with a dash '-' or a bang '!' it will still think there is a flag there.

---

### Post by cheruvim on 2008-07-02
actually with a bang '!' it does a history lookup.. usually doesn't find the entry for whatever it is that follows that bang and then spits out an error

---

