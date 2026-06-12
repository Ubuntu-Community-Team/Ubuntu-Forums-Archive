---
title: "terminal"
date: 2008-03-24
forum: General Help
---

### Post by balagunner on 2008-03-24
When I download anything using apt-get install or using youtube downloader after the downloads I don't know where it is saved and I cannot access.

Please help.

---

### Post by sumguy231 on 2008-03-24
When you install a program with apt, then it should show up in the Applications or System menu if it is a graphical program, or you can usually run it from the run dialog (Alt+F2) or the terminal by typing the program's name. 

I don't know anything about Youtube Downloader, is that a Firefox extension? If so, Firefox downloads to your home directory by default.

---

### Post by StOoZ on 2008-03-24
or you can use (not always) the following command:
> whereis 'packagename'

---

### Post by zvacet on 2008-03-24
```
locate **packagename**
```


or go othte top of filesystem with **cd /** and type

```
sudo find / -name *package*
```

---

