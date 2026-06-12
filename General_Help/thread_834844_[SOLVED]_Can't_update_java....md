---
title: "[SOLVED] Can't update java..."
date: 2008-06-19
forum: General Help
---

### Post by Magoffire on 2008-06-19
I downloaded the JDK 6, update 6 through both the package manager and the sun website.

In both cases, I got the same resolve.

After installation, my computer still uses java 1.5.0 as the default (Hardy).

I added the jdk's "bin" folder to the system "PATH" variable.  But that still didn't work.

The issue I am trying to fix is a freezing swing GUI, someone told me download/installing the new JDK fixed it for him.

Any advice would be much appreciated.

~ Mike

---

### Post by jamesstansell on 2008-06-19
After installing the sun-java6-jre package you may need to run ```
$ sudo update-java-alternatives -s java-6-sun
```

If you still have problems then please post the output from this command:
```
$ /usr/lib/jvm/java-6-sun/jre/bin/java -version
```

---

### Post by Magoffire on 2008-06-20
> **jamesstansell said:**
> After installing the sun-java6-jre package you may need to run ```
$ sudo update-java-alternatives -s java-6-sun
```

If you still have problems then please post the output from this command:
```
$ /usr/lib/jvm/java-6-sun/jre/bin/java -version
```

That terminal command fixed it.  Thanks man!

SOLVED!

---

