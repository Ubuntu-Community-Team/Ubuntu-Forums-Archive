---
title: "100% Waiting on headers? stuck on apt-get update also unable to empty trash can argh"
date: 2014-07-20
forum: General Help
---

### Post by phat2 on 2014-07-20
please help having some seriously annoying issues unable to complete update when launching apt-get update just sticks on 
100% [Waiting on headers]

 also another issue not emptying a trashcan is related to bleach bits trash it was a huge file tht i had to manually delete now to huge but 0 bytes files stuck tried Midnight Commander with no success please respond an thanks in advance!

---

### Post by silex89 on 2014-07-20
Hi there! :)

I had that issue yesterday. I cancelled the procedure by hitting Ctrl-C. Then I tried to hit a sudo apt-get dist-upgrade and there was no issues. The package databases update properly. I guess the SIGTERM doesn't reach the process and that's why it never "finishes" (although I already know that it did).

I'm sorry. I don't know how to solve the thrash issue...But hang in there.

Best of luck! :D

---

