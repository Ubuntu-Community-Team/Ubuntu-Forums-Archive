---
title: "bjobs and bkill"
date: 2008-04-15
forum: General Help
---

### Post by cybo on 2008-04-15
one of my friends ran a batch of jobs. later he wanted to kill all of them at once. all of his jobs started with a 397 id. i recommended to do the following:

bjobs | cut -f1 | grep 397 | bkill

but for some reason bkill would not accept it.

i know that bjobs and bkill are not ubuntu commands (at least i think so). can anyone explain what happened? why it wouldn't accept input. i'm new to linux myself, started using it about couple of months ago, so there wasn't much help from me when we got the error.

thank you ahead of time.

---

