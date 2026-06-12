---
title: "How to test a patch for X composer"
date: 2016-03-15
forum: General Help
---

### Post by mats-gbproject on 2016-03-15
Hi

I tried to make a patch for new composers, it is here:
[https://bugs.freedesktop.org/show_bug.cgi?id=93660](https://bugs.freedesktop.org/show_bug.cgi?id=93660)

I made it to make it possible to use a new keyboard here:
[https://bugs.freedesktop.org/show_bug.cgi?id=92344](https://bugs.freedesktop.org/show_bug.cgi?id=92344)

I can add the keyboard, and after I can add this line the terminal to flush keyboard settings and then start to use the new keyboard:
sudo dpkg-reconfigure xkb-data

However, the composer is not working, and I wonder if it is because I need to flush & reload some composer settings?

Do anyone have any leads for me?

---

