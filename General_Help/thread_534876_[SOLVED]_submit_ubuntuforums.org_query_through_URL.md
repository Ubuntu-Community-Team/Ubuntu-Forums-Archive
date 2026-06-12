---
title: "[SOLVED] submit ubuntuforums.org query through URL?"
date: 2007-08-25
forum: General Help
---

### Post by geraschenko on 2007-08-25
I realize this is probably not the right place to ask the following question, but I don't know where else to ask.

I like konqueror's web shortcuts. If I type "wp:pineapple" into my location bar, I get sent to
[http://en.wikipedia.org/wiki/Special:Search?search=pineapple&go=Go](http://en.wikipedia.org/wiki/Special:Search?search=pineapple&go=Go)
and I can read all about pineapples. If I find a site I like, then I can make a new web shortcut "mysrch" by telling konqueror that the URI for this shortcut is
http://somesiteIlike.com/?search=\{@\}
Then when I type "mysrch:asdfasdf" in my location bar, I get sent to
[http://somesiteIlike.com/?search=asdfasdf](http://somesiteIlike.com/?search=asdfasdf)

However, I can't seem to get a shortcut working for an ubuntuforums.org search because the search isn't stored in the URL in any way that I can see. In Firefox, I can get the desired result by right-clicking on the search field and selecting "Add a Keyword for this Search". Does anybody know how to submit a query to ubuntuforums.org through the URL?

---

### Post by aysiu on 2007-08-26
I don't know about Konqueror, but Opera uses this for the address: ```
http://ubuntuforums.org/search.php?do=process
``` and then this for the query string ```
query=%s&s=&do=process&forumchoice%5B%5D=&childforums=1&exactname=1&op=
```

---

### Post by geraschenko on 2007-08-26
Thanks. That did the trick (substituting "\{@}" for "%s").

---

