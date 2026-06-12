---
title: "Choosing which version of Java"
date: 2014-06-08
forum: General Help
---

### Post by orrymr on 2014-06-08
Hi guys,

I'm trying to set java so that it works with java7 as opposed to the default 1.6. I've downloaded the java7 sdk and added it to my PATH, before /usr/bin where the link to java1.6 is kept. I thought that since I added the java7 directory to PATH before /usr/bin, when I ran either java or javac, it would look in that directory first - but this doesn't seem to be the case.

Any suggestions?

---

### Post by orrymr on 2014-06-08
Well, that was an hour worth of relentless frustration caused by doing this: PATH=JAVA_HOME/bin:$PATH
instead of this PATH=$JAVA_HOME/bin:$PATH

I hate everything right now. :evil:

---

