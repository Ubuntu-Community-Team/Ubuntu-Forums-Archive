---
title: "where can i download cedega or wine???"
date: 2005-09-14
forum: General Help
---

### Post by jervine on 2005-09-14
guys... kindly give me some links on where to get the cedega or wine, need it badly

---

### Post by FLeiXiuS on 2005-09-15
Cedega -- [www.transgaming.org](www.transgaming.org) -- You'll have to purchase the binary packages or you could compile from CVS.  A great how to for how to actually do this can be found here.  [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

Or, you have another option.  You can apt-get install Wine simply by adding they're repositories to your apt sources.

```

sudo gedit /etc/apt/sources.list

```
Add the following lines...
```

# Wine-HQ
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```
Now update your sources and install!
```

sudo apt-get update
sudo apt-get install wine

```

Thats all of the information I can give.  Any more questions drop me a message or post it.

---

