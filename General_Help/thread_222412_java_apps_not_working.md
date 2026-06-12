---
title: "java apps not working"
date: 2006-07-24
forum: General Help
---

### Post by Rule on 2006-07-24
hey, when I run limewire or azureus I keep getting this output even if I install the sun-java package in synaptic

Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


and I did make sure the java jre package.

---

### Post by Skia_42 on 2006-07-25
What does > java -versiongive you?

---

### Post by Jagot on 2006-07-25
If it gives you something other than Sun's Java then use this to select the correct one:

```
sudo update-alternatives --config java
```

---

