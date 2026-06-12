---
title: "Bash Scriptig xml parse"
date: 2016-02-03
forum: General Help
---

### Post by jimmyh1972 on 2016-02-03
Hi , I have this xml file:
<user>
  <item> 
    <site>https://www.yahoo.com</site>
  </item>
</user>
and I want firefox to redirect to the url parsed from this xml file
I write the command - xmlstarlet sel -t -m '//site' -v . -n <data.xml
It parses the url but when I write "firefox xmlstarlet sel -t -m '//site' -v . -n <~/Desktop/data.xml"
It doesn't redirect to the url
How can I do it?

---

### Post by steeldriver on 2016-02-03
You probably want [I]command substitution
[/I]
```

firefox [COLOR=#0000ff]**$(**[/COLOR]xmlstarlet sel -t -m '//site' -v . -n <data.xml[COLOR=#0000ff]**)**[/COLOR]

```

---

### Post by jimmyh1972 on 2016-02-03
Tnx!!! it works good

---

