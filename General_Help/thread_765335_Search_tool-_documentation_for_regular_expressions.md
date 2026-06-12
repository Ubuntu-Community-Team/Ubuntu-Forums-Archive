---
title: "Search tool- documentation for regular expressions?"
date: 2008-04-24
forum: General Help
---

### Post by stair314 on 2008-04-24
You know the "Search for files..." application under the "Places" menu in Ubuntu 7.10? Is there documentation for the syntax for the regular expressions it uses anywhere?

---

### Post by prshah on 2008-04-24
> **stair314 said:**
> You know the "Search for files..." application under the "Places" menu in Ubuntu 7.10? Is there documentation for the syntax for the regular expressions it uses anywhere?

```
man regex
```?

---

### Post by stair314 on 2008-04-24
That's not quite what I'm looking for; I just want to know what characters it supports, like "*". "?", etc. Is it just meant to be the same as the bash shell?

---

### Post by prshah on 2008-04-25
> **stair314 said:**
> That's not quite what I'm looking for; I just want to know what characters it supports, like "*". "?", etc. Is it just meant to be the same as the bash shell?

Yes, it is similar to the wildcards used in bash shell, but search for files will only use *,[, and ].
Example:
> 
*.[ch] will find all files ending in either ".c" or ".h".

---

