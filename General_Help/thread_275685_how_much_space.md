---
title: "how much space"
date: 2006-10-11
forum: General Help
---

### Post by mitjab on 2006-10-11
how i can see from console how much space i have in my disk and in my account?

thx

---

### Post by aysiu on 2006-10-11
```
df -h
```

---

### Post by dagnabit dang doohickey on 2006-10-11
[This]("http://www.debian-administration.org/articles/143") may be a little more than you were asking for, but it's a good article.

---

### Post by mitjab on 2006-10-11
thx, how can i see how user account use space?
df -h is for whole disk, what is for useraccount.

thx

---

### Post by dagnabit dang doohickey on 2006-10-11
du -hs /home/*username*

If you have many users on your system, instead of running the above command over and over, you can run the following:

du -h --max-depth=1 /home 

[Here's]("http://www.codecoffee.com/tipsforlinux/articles/22.html") some info on the du command.

---

