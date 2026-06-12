---
title: "Change Search Engine URL?"
date: 2013-06-04
forum: General Help
---

### Post by EchoTech on 2013-06-04
Ubuntu 13.04 & Firefox v21.0  & NoScript 2.6.6.2uses

  I use DuckDuckGo as my search engine in Firefox.  By default DuckDuckGo uses [https://duckduckgo.com/?q=ubuntu](https://duckduckgo.com/?q=ubuntu) (q=[search term]).  With NOScript active his leads to a page that says among other things "Page Requires Javascript  Click Here For Non JS".  The "Here" URL is [https://duckduckgo.com/html/?q=ubuntu](https://duckduckgo.com/html/?q=ubuntu).  I would like (if possible) to change the "https://duckduckgo.com/?q=" to "https://duckduckgo.com/html/?q=" to avoid one whole mouse click.  I didn't see anything in "about:config".

  Thanks in advance and I'll be back in about 24 hours, life is getting in my way.

---

### Post by Habitual on 2013-06-04
So, issue an allow for duckduckgo.com

---

### Post by MidnightGrey on 2013-06-04
You can add an exception in NoScript like Habitual said, or modify the firefox variable like so:

about:config > locate the variable "keyword.URL" > modify the string.

---

### Post by Habitual on 2013-06-04
[http://kb.mozillazine.org/Keyword.URL#Possible_values_and_their_effects](http://kb.mozillazine.org/Keyword.URL#Possible_values_and_their_effects)

I still had to issue an allow after those changes, even though I had allowed ddg previously.
Once I did, it seemed to work (I got results) as expected.

---

### Post by EchoTech on 2013-06-05
Thanks all.  Changing "keyword.url" seems to have done what I want.

---

### Post by EchoTech on 2013-06-05
Forgot  ...And allow DuckDuckGo in Noscript.

---

