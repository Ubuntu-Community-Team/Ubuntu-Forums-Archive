---
title: "pstoedit doesn't work"
date: 2008-04-19
forum: General Help
---

### Post by Ampi on 2008-04-19
i installed the command pstoedit, but everytime I run it the command just won't finish so my file.ps will not be converted to file.fig.

I use the following commands:

```
# pstoedit -f xfig ~/file.ps ~/file.fig
```

and

```
# pstoedit -f fig "r600x600" file.ps file.fig
```

In both cases the command runs eternally saying 

```
pstoedit: version 3.44 / DLL interface 108 (build Apr 29 2007 - release build -
g++ 4.1.3 20070423 (prerelease) (Ubuntu 4.1.2-3ubuntu3)):
Copyright (C) 1993 - 2006 Wolfgang Glunz

```

and a empty file file.fig is created. 

Any idea how I can solve this?

---

