---
title: "Copy web files"
date: 2007-04-25
forum: General Help
---

### Post by badhat on 2007-04-25
This is not specifically a Ubuntu question, but:

How do I copy a net file, using the url?  I want to do something like:

   ```
cp `http://a28.org/images/a28.gif` ./a28.gif
```

The 4nt shell under Windows can do it.

badhat

---

### Post by aidanr on 2007-04-25
```
wget [http://a28.org/images/a28.gif](http://a28.org/images/a28.gif) -O ~/a28.gif
```

see "man wget" for more info

---

### Post by badhat on 2007-04-26
Thanks aidanr!
Yes I just read the man page. Excellent!

---

### Post by leg on 2007-04-26
Not sure if this will be any use to you but have a look a [scrapbook]("https://addons.mozilla.org/en-US/firefox/addon/427").

---

