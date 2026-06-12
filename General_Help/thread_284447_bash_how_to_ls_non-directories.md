---
title: "bash: how to ls non-directories?"
date: 2006-10-25
forum: General Help
---

### Post by Westerberg on 2006-10-25
In a directory with a mix of subdirectories and regular files,
how can I list nondirectories using bash's 'ls' command?
I can list all directories using ```
ls -d */
```But ```
ls -d *[!/]
``` doesn't return any matches. 
I know I could accomplish this using ```
find . -maxdepth 1 -type f
```
but isn't there a way using ls in concert with regular expressions or pipes?

---

### Post by Ramses de Norre on 2006-10-25
Maybe this:
```
ls -la|grep -v ^d
```
I don't know whether this is what you're looking for..

---

### Post by Westerberg on 2006-10-25
I guess so.  
It just seems lacking that ls has no option to list *only* regular files, or *only* directories, or *only* symbolic links, etc.  I would have thought such features would have long ago been added.
And I can't figure out for the life of me why ```
ls -Fd *[!/]
``` won't list nondirectories!

---

### Post by Ramses de Norre on 2006-10-25
Because bash doesn't interpret "!" as a negation..

---

