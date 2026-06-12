---
title: "need help installing java for google chrome"
date: 2015-05-21
forum: General Help
---

### Post by kaitlin3 on 2015-05-21
ok so im using Lubuntu 15.04 trusty and heres my java version

 java version "1.7.0_79"OpenJDK Runtime Environment (IcedTea 2.5.5) (7u79-2.5.5-0ubuntu1)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)

any idea how to add a java plugin to google chrome?

---

### Post by dino99 on 2015-05-21
chromium is a supported ubuntu package, but chrome is a closed one

---

### Post by monkeybrain20122 on 2015-05-21
Won't work, google has removed support for plugins in its browsers (Chrome or Chromium, doesn't matter) , the goal is to phase out plugins completely, this happened in Linux last year, it will hit Windows and Mac by the end of the year.

---

### Post by monkeybrain20122 on 2015-05-21
> **dino99 said:**
> chromium is a supported ubuntu package, but chrome is a closed one

Who cares what is supported Ubuntu package? This is not what OP asked. Chromium is also outdated and buggy alpha release. :)

---

### Post by kaitlin3 on 2015-05-21
so what do i do if i visit a site that requires java

---

### Post by monkeybrain20122 on 2015-05-21
Use Firefox 

edited: and install java plugin

```
sudo apt-get install icedtea-plugin
```

Then restart FF.

---

### Post by kaitlin3 on 2015-05-21
ok well how do i add java to firefox

---

### Post by monkeybrain20122 on 2015-05-21
See my edit.

---

### Post by slickymaster on 2015-05-21
> **monkeybrain20122 said:**
> Won't work, google has removed support for plugins in its browsers (Chrome or Chromium, doesn't matter) , the goal is to phase out plugins completely, this happened in Linux last year, it will hit Windows and Mac by the end of the year.Yeap, that's true. In the Java plugin specific case, Google announced in September 2013 plans to remove NPAPI support from Chrome by "the end of 2014", thus effectively dropping support for Silverlight, Java, Facebook Video and other similar NPAPI based plugins, and as of April 2015, starting with Chrome Version 42, Google has added an additional step to configure NPAPI based plugins like Java to run.

More information [here]("http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html").
> **monkeybrain20122 said:**
> Use Firefox.@kaitlin3:
I think that what monkeybrain20122 means is that Oracle's official position is that Firefox is the recommended browser for Java on Linux.

---

