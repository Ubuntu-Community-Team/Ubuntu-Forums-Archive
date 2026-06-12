---
title: "Link pathing"
date: 2008-02-19
forum: General Help
---

### Post by Xceptiona1 on 2008-02-19
I am attempting to create some shortcuts/links on my desktop to some manually placed/installed games. If I execute the .bin file from the folder it's in then all is well, however if I create a link to that file on my desktop then it errors out because it can't find certain files. I'm thinking some sort of pathing needs to be added to the link, but I can't figure out how to do that. Thank you

Brad

---

### Post by dcstar on 2008-02-19
> **Xceptiona1 said:**
> I am attempting to create some shortcuts/links on my desktop to some manually placed/installed games. If I execute the .bin file from the folder it's in then all is well, however if I create a link to that file on my desktop then it errors out because it can't find certain files. I'm thinking some sort of pathing needs to be added to the link, but I can't figure out how to do that. Thank you

Brad

Create an executable script that cd's to the required directory, and link to that.

---

### Post by erfahren on 2008-02-19
what you can also do is this - just create a launcher and for the command put:
```

sh -c "cd /path/to/directory && ./filename.bin"

```
(see [this thread](http://ubuntuforums.org/showthread.php?t=673809) )

---

