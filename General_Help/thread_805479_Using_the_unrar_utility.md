---
title: "Using the unrar utility"
date: 2008-05-24
forum: General Help
---

### Post by armitage1337 on 2008-05-24
Hi,

Does anyone know if it's possible to specify the directory to which a file should be unrar'd? From what the help file says, it's only possible to unrar to the current directory. Any ways around this without writing a wrapper script?

Thanks in advance for the help!!

---

### Post by olejorgen on 2008-05-24
```

$ unrar --help

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> **<path_to_extract\>**
# ...

```
So:
```

unrar e myrarfile.rar my/path/

```

---

