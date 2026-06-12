---
title: "List only directories"
date: 2016-04-03
forum: General Help
---

### Post by vasa1 on 2016-04-03
While trying to help out here, I came across [http://stackoverflow.com/questions/14352290/listing-only-directories-using-ls-in-bash-an-examination](http://stackoverflow.com/questions/14352290/listing-only-directories-using-ls-in-bash-an-examination)

As an example,
```
ls -d /usr/share/themes/*/
``` or ```
ls -d /usr/share/themes/*/*/
``` and so on to go deeper.

I liked this answer as well: [http://stackoverflow.com/a/17009555](http://stackoverflow.com/a/17009555) where *echo* gives a somewhat more spartan output.

---

### Post by sudodus on 2016-04-04
You can try ***find*** too, for example ```
find . -type d
```

---

