---
title: "Java Problem in Hardy"
date: 2008-07-04
forum: General Help
---

### Post by HexJunkie on 2008-07-04
I've installed the sun-java-6-jre package (and it's dependencies), but when I run "java -version", it still says that I am using gij.

Do I need to do something else to get rid of gij and use the Sun Java implementation?

I also tried installing sun-java-5-jre.

---

### Post by jamesstansell on 2008-07-04
You have several choices, but this is the closest to what you requested.
```
$ sudo update-java-alternatives -s java-6-sun
```

---

