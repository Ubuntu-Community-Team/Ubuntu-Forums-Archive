---
title: "How to remove a link name &quot;*&quot;?"
date: 2018-09-08
forum: General Help
---

### Post by monkeybrain20122 on 2018-09-08
Hi, I have an odd problem. When I tried to create a symlink to /usr/local/lib I made a mistake and created a dead link called *. Now I want to remove it but it seems that sudo rm * would remove everything. 

How should I remove it, or should I just leave it there since it does nothing.

Thanks

---

### Post by sisco311 on 2018-09-08
Check out: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

You can use single quotes, double quotes or a backslash in order to tell to the shell to threat `*' literally. :)

The rm command has a very useful `-i' flag. You can use it to make sure that you are deleting the right file.

---

### Post by monkeybrain20122 on 2018-09-08
It works, thanks!

---

