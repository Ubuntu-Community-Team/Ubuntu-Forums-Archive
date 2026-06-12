---
title: "[Solved] Latex and url.sty"
date: 2008-05-29
forum: General Help
---

### Post by diafanos on 2008-05-29
I found out a problem with the url.sty file of texlive-xetex package.

The version of this file is old(v3.2) and when you try to run xetex command, an error occurs. The problem has something to do with some non-ASCII characters in the file.

To solve the problem just go to:
```

[http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=url]("http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=url")

```

download it and replace the previous url.sty in 

```

/usr/share/texmf-texlive/tex/latex/ltxmisc

```

The version of the new one is 3.3.

---

