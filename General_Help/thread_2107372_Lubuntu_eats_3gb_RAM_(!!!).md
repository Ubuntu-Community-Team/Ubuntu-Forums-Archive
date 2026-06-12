---
title: "Lubuntu eats 3gb RAM (!!!)"
date: 2013-01-21
forum: General Help
---

### Post by F i L on 2013-01-21
What happened? I just installed apache/php/mysql to edit my website and at some point I saw from lxtask that the system used 4gb RAM. Initially, I thought of a zombie process so I rebooted the system but again, when lubuntu just starts free -m shows that 3gb ram is used. More bizzare is the fact that from lxpanel I can't see which process consumes all that RAM.

Does anyone have any idea where my RAM is used?

My dmesg: [http://pastebin.com/bZ1XjwmH](http://pastebin.com/bZ1XjwmH)
A screenshot of lxpanel: [http://postimage.org/image/7wwvxuag5/](http://postimage.org/image/7wwvxuag5/)

If anyone needs anything that might be useful just ask me!

---

### Post by F i L on 2013-01-21
I found the answer using top. Interestingly enough, top shows me more info on the running processes. The process that ate me 2.8Gb RAM was cassandra database which I installed about a couple days ago to learn a bit about non relational databases:D

---

