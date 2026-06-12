---
title: "run set-uid shell program in ubuntu and set premission 4755"
date: 2013-11-08
forum: General Help
---

### Post by salehi.information on 2013-11-08
hi dear's,
how i can Run Set-UID shell programs in ubuntu 12.10,
and then, how i can  copy /bin/zsh to /tmp, and make it a set-root-uid program with permission 4755????

---

### Post by salehi.information on 2013-11-08
hi dear's,
how i can Run Set-UID shell programs in ubuntu 12.10,
and then, how i can  copy /bin/zsh to /tmp, and make it a set-root-uid program with permission 4755????

---

### Post by Impavidus on 2013-11-08
[http://www.faqs.org/faqs/unix-faq/faq/part4/section-7.html](http://www.faqs.org/faqs/unix-faq/faq/part4/section-7.html)

Seems to be risky.

---

### Post by Lars Noodén on 2013-11-08
What are you trying to accomplish?  SUID is almost always the wrong way to go about things and /tmp is usually the wrong place for executable files.  There's probably a better way to solve the problem if you can tell us what it is.

---

### Post by lykwydchykyn on 2013-11-08
:confused::confused:

Are you *trying* to make your system insecure?

---

### Post by cariboo on 2013-11-09
Moved to General Help, as this is a support question.

---

### Post by coffeecat on 2013-11-10
Threads merged. Please do not post duplicate threads.

---

