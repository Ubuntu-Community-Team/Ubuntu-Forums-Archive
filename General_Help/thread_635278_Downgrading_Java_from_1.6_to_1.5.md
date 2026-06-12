---
title: "Downgrading Java from 1.6 to 1.5"
date: 2007-12-08
forum: General Help
---

### Post by JuanChanKane on 2007-12-08
Hola!

I am migrating out of XP and into Gutsy, all works rock solid so far!!! Anyway I use a web application that is compatible with Java SE 1.5.x instead of 1.6 that I got installed. 

Any idea on how to downgrade Java to 1.5?  Im no expert with source files & compilation, maybe there are binaries for Gutsy?

Thanks for reading! :guitar:

---

### Post by taurus on 2007-12-08
```
sudo apt-get update
sudo apt-get remove sun-java6-bin sun-java6-jre sun-java6-plugin
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin
java -version
```

---

### Post by JuanChanKane on 2007-12-08
Worked like a charm, thanks Taurus!

Im really getting close to kissing my XP goodbye now. :guitar:

---

