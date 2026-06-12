---
title: "bash bug?"
date: 2007-10-22
forum: General Help
---

### Post by Westerberg on 2007-10-22
From the bash man pages:
>  Composite patterns may be formed using one or more of the following sub-patterns:
. . . 
 !(pattern-list)
                     Matches anything except one of the given patterns

In other words, you can exclude all patterns except the few you want.
E.g., in a directory containing a mix of .html, .pdf, .avi, and .txt files, you should be able to delete all files except *html by entering:
```
rm !(*html)
```
I used to do this all the time when I had Feisty.
Since upgrading to Gutsy, the result of the above is:
```
james@james-desktop:~/Documents$ rm !(*html)
bash: !: event not found

```
Anyone know what's going on?

---

### Post by nick_h on 2007-10-23
Just before your quote from the man page it says:
> If the extglob shell option is enabled using the shopt builtin, several extended pattern matching operators are recognized.
Try typing:
```
shopt
```
from the command prompt to check if extglob is enabled.

---

