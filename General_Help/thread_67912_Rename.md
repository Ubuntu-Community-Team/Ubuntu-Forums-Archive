---
title: "Rename?"
date: 2005-09-21
forum: General Help
---

### Post by tom-ubuntu on 2005-09-21
Sorry, for this question. I remember using the "rename" command for example like the following:

```
rename "The Simpons" "Simpons" *
```

This ends up chaninge all the filenames from "The Simpsons..." episodes to "Simpons...". But now i just receive the following error message:

```
Can't locate object method "Die" via package "S" (perhaps you forgot to load "S"?) at (eval 1) line 1.
``` 

Do I miss something? What has changed? Haven't used if for a while, but still.... I am confused.... 

Thanks for any reply!
Joe

---

### Post by bsussman on 2005-09-21
The proper command on my system would be:

 ```
> rename 's/The\ Simpsons/Simpsons/' *
``` 

as the manpage says:

"rename" renames the filenames supplied according to the rule specified
       as the first argument.  The perlexpr argument is a Perl expression which
       is expected to modify the $_ string in Perl for at least some of the
       filenames specified.

thus (the filename The\ Simpsons1 is a red herring thrown in in case you have not had lunch):
 ```
bos@Dillon:~/xxx$ touch "The Simpsons1"
bos@Dillon:~/xxx$ ls
The Simpsons1  The\ Simpsons1  yx1  yx12  yx123
bos@Dillon:~/xxx$ touch "The Simpsons2"
bos@Dillon:~/xxx$ rename 's/The\ Simpsons/Simpsons/' *
bos@Dillon:~/xxx$ ls
Simpsons1  Simpsons2  The\ Simpsons1  yx1  yx12  yx123
```

---

