---
title: "no improvements with multiple pthreads"
date: 2013-10-24
forum: General Help
---

### Post by maddy2 on 2013-10-24
I have program with with multiple pthreads and I don't see an improvements with multiple threads.
Can you help me understand the below execution times for my programs.

1 thread = 59 seconds
2 thread = 30 seconds
3 thread = 30 seconds
4 thread = 30 seconds

---

### Post by Impavidus on 2013-10-24
It depends on what the program is doing and on the kind of processor you have. If execution of the program cannot be efficiently split in more than two threads you won't see much increase in performance when adding a third. If you have a dual core processor adding a third thread does gain you much, as the threads cannot be executed at the same time.

---

