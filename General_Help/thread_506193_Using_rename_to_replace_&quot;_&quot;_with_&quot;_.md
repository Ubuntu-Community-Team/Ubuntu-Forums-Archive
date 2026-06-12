---
title: "Using rename to replace &quot; &quot; with &quot;_&quot;"
date: 2007-07-21
forum: General Help
---

### Post by AxAeo on 2007-07-21
I recently copied a lot of files from my Windows partition, and a lot of them have names which include spaces. I'm trying to use rename to do it, but I don't think I'm entering the Perl expression correctly. I tried something like this:

```
rename -v s'/\ /_' * 
```

but got this:

"Substitution replacement not terminated at (eval 1) line 1."

Can anybody point me in the right direction here?

---

### Post by vanadium on 2007-07-21
You just forgot the third slash. Moreover, your command will only find/replace the first space. To have all spaces replaced, you need to specify the g of global after your third slash. The command becomes:

```

rename 's/\ /_/g' *

```

Do you know of the -n option? This option will print the names without actually performing the rename, good for testing!

---

