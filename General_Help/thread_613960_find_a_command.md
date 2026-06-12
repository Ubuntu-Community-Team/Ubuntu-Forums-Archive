---
title: "find a command"
date: 2007-11-15
forum: General Help
---

### Post by oneadvent on 2007-11-15
I want to find a program named atoms somewhere on my system, but I do not have the foggiest idea where it is.

This is a custom build, not really Ubuntu, so it needs to search the whole system.

Does anyone know how to do this?

PS: it works from anywhere, not user centric.

Thanks for anyones help with this.

Josh

---

### Post by JasonF on 2007-11-15
The command which in a shell will tell you the location of the binary that will be run when searching the path. For example 'which bash' on my system will print /bin/bash.

---

### Post by bingoUV on 2007-11-15
```

locate -i atoms

```

If the above command gives too many results, 
```

locate -i atoms | grep -i bin

```

If the above two do not work due to lack of locate database, 
```

find / | grep -i atoms | grep -i bin

```

---

### Post by oneadvent on 2007-11-15
fantastic, 2nd command above worked like a charm.

That will help out tremendously. Thanks!

---

