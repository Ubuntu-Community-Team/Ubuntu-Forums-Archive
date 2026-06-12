---
title: "new, uglier, fonts after xgl/compiz install"
date: 2006-08-25
forum: General Help
---

### Post by cptjaben on 2006-08-25
after installing xgl/compiz using [this]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper") guide , the fonts seemed to have changed to fonts that are noticeably uglier. does anyone know how to fix this?

Thanks,
cptjaben

---

### Post by Fass on 2006-08-25
[http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238) <- "Official" downgrade fix
[http://www.compiz.net/topic-3116-11.html](http://www.compiz.net/topic-3116-11.html) <- Fixed debs for fonts in first as well as second post on that page. (The first post, 151, has bytecode interpreter and cleartype-like patches, while the second, 152, "only" has the bytecode interpreter patch). 

Pick either of those fixes - the first thread will fix your libvte problems, too, if you have those (like, Synaptic not starting).

Let me guess, you used the [http://xgl.compiz.info/](http://xgl.compiz.info/) repos? Those are broken and outdated. You should use one of these:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

For keys do:

```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
```

---

