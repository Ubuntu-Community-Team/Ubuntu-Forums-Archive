---
title: "[SOLVED] Smart cp with unison or rsync"
date: 2008-03-14
forum: General Help
---

### Post by geo909 on 2008-03-14
Hello everybody,

Is there an equivalent to cp but in a smart way via **command line**?
I mean, not to copy things that are already in the destination file.

I do NOT mean synchronizing the two folders, just copy-pasting the source in a time-saving way..

 That can be done easily with unison:
```

unison /source/folder /destination/folder -ui text
```

and then type 
```
>
```
 in each question, in order to give the "--->" direction.

The thing is that I want to write a script so I would like to do things silently.
If I add the```
-silent
``` option, unison will just synchronize the two folders..

Is there a way to give the direction from the beginning?
Something like 
```
unison source/folder -> destination/folder 
```  thing?!

 Thank yoou  in advance for your time!

---

### Post by kevdog on 2008-03-14
you mean more than using the --force <root> option that will force one root to be master and the other slave?

---

### Post by geo909 on 2008-03-14
Thanks for taking the time to answer.

> **kevdog said:**
> you mean more than using the --force <root> option that will force one root to be master and the other slave?

Well, to be honest I installed unison 2 hours ago and I am not very familiar with it. Keep reading the help files, though.

 What's with the "--force <root>" option? Is that a cp equivalent?

How should I type it? Something like:

```

unison /source/folder /destination/folder --force /source/folder -silent -ui text

```
would do my job or should I change anything?

---

### Post by geo909 on 2008-03-14
Yes, that did the job!
I run a test and 

```
unison /source/folder /destination/folder -force /source/folder -silent -ui text
```

is exactly the smart copy-paste equivalent i was seeking for..

Thanks a lot!

---

### Post by kevdog on 2008-03-14
Your syntax is correct, you might want to investigate the creation of prf or preference files if you need different options for different archives.

---

