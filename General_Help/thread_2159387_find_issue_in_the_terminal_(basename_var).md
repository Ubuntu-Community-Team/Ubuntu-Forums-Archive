---
title: "find issue in the terminal (basename var)"
date: 2013-07-02
forum: General Help
---

### Post by mbnoimi on 2013-07-02
Howdy?

I want convert all *.properties files to *.po but the following script adds .po to extension instead of replacing .properties:
```
#!/bin/bash
# I get common.properties.po instead of common.po !!!
find ./ -name "*.properties" -exec prop2po --input '{}'  --output '{}.po' --encoding utf-8 \; 

```

How can I fix this issue?

P.S. I think this issue related to base name of the file but I don't know how to apply it to find command

---

### Post by Vaphell on 2013-07-02
```
#!/bin/bash

while read -rd $'\0' f
do
  prop2po --input "$f" --output "${f%.*}.po" --encoding utf-8
done < <( find -name "*.properties" -print0 )
```

---

### Post by mbnoimi on 2013-07-02
Thanks a lot

---

