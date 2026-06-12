---
title: "How to add list of PPAs"
date: 2013-12-14
forum: General Help
---

### Post by sandyd on 2013-12-14
Is there some way I can have apt-add-repository add a list of PPAs (i.e. below) from a file?
PPAs will be one each line.

```

ppa:sandyd/openlitespeed-stable
ppa:sandyd/openlitespeed-stable2
..etc

```

---

### Post by steeldriver on 2013-12-14
Would a loop work?

```
while read -r ppa; do add-apt-repository "$ppa"; done < *file*
```

---

