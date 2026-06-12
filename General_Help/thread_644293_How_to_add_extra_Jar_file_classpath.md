---
title: "How to add extra Jar file classpath"
date: 2007-12-18
forum: General Help
---

### Post by ahjiefreak on 2007-12-18
Hi,

I have a problem where I would like to add an extra jar wrapper to classpath in my bashrc in my linux box.


Something like:-

export CLASSPATH=/home/test/test.jar:/home/test/private.jar:$CLASSPATH

Where the second jar file (private.jar) is the one that I would like to point to as well when test.jar is loaded.

It doesnt work as it still load the first test.jar only. 

When I do echo $CLASSPATH, it points me to first jar file but not both.

Please help.

Thanks.

-Jason

---

### Post by taurus on 2007-12-18
Is that a typo because I see an extra space between **private.j** and **ar**, private.j ar?

---

