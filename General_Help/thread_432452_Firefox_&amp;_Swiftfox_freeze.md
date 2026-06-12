---
title: "Firefox &amp; Swiftfox freeze"
date: 2007-05-04
forum: General Help
---

### Post by DougieFresh4U on 2007-05-04
Feisty we are talking about here. When my desktop comes up and I click to open Firefox or Swiftfox, they open but a blank white page appears and freeze up. no home page. I can open other apps ok. I opened terminal and typed Firefox and Firefox opened to blank white page and froze also. Please, any one have any clue as to what is going on or what I should be looking for/:confused:**EDIT:** I can open Internet Explorer and it function as normal IE gets in Ubuntu.

---

### Post by spin2cool on 2007-05-04
make sure no previous instance of firefox is running:

```
ps aux | grep firefox
```

If it is running, kill it. 

```
kill -9 <process #>
```

If that isn't the problem, try creating a new profile:

```
firefox -p
```

---

