---
title: "What does the symbolic link 'lock' means in Mozilla Firefox folder?"
date: 2017-02-08
forum: General Help
---

### Post by bernjul on 2017-02-08
There are a couple of files in my Mozilla/Firefox folder I'm very suspicious about. What is this symbolic link 'lock' with full rights for everybody? I can't change the rights, I get the message that this file can't be handeled and it would link to nowhere. When I delete it, it gets restored next time I start firefox. When I google I find absolutely nothing about it. Who knows this file and what it is about?

---

### Post by r.stiltskin on 2017-02-08
Nothing to be suspicious about -- the running instance of firefox places the lock file there to prevent the possibility of a second firefox process trying to make modifications to the same firefox profile.

---

### Post by bernjul on 2017-02-09
Thank you very much for this answer.

---

### Post by oldos2er on 2017-02-09
If your question is answered to your satisfaction, please mark your thread 'Solved' using Thread Tools at the top of the page. It'll help others who might have the same question. Thanks!

---

