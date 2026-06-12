---
title: "xmlling and CDATA"
date: 2013-08-03
forum: General Help
---

### Post by denarced on 2013-08-03
Hello,

**The problem**
xmllint does not indent xml files in a proper way. The end tag after character data which is not enclosed inside CDATA section is not indented. With the CDATA markup everything's good.

Is this normal behavior? I checked the man page but it barely said anything about indenting. I don't have any experience with other xml "beautifiers", do they behave in the same way?
If you want try this out, grab the xml files([withCdata]("http://pastebin.com/6UBHwCjX"), [woCdata]("http://pastebin.com/8Ljggtgv")) and run the following commands:
```

xmllint --format --recover withCdata.xml
xmllint --format --recover woCdata.xml

```

---

