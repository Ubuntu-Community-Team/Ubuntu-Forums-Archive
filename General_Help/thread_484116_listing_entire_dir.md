---
title: "listing entire dir"
date: 2007-06-25
forum: General Help
---

### Post by prezbedard on 2007-06-25
The contents of my /etc is so much so that when I use ls to view it I can never see the entire contents of the directory. Is there a way to do this or to a page by page view sort of like you can with windows when there is such a large listing?

I read the man page but couldn't find anything.

Thanks,

---

### Post by DarkN00b on 2007-06-25
You can use:

```
ls -a |less
```

or 

```
 ls -a |more
```

The | is a pipe symbol. | = shift+\

You could also do 

```
ls -a > ~/etc.txt
``` to output the directory listing to a text file in your home directory.

---

### Post by prezbedard on 2007-06-26
Thanks!

I knew there had to be a way.

---

