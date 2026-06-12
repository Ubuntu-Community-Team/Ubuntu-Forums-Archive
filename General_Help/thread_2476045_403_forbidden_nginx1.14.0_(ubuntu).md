---
title: "403 forbidden nginx/1.14.0 (ubuntu)"
date: 2022-06-15
forum: General Help
---

### Post by chat-4432 on 2022-06-15
when i run docker 
i got this error messages
```
403 forbidden nginx/1.14.0 (ubuntu)
```
on localhost:8080
what should i do ??

---

### Post by yancek on 2022-06-15
I've not used docker or ngnix but a quick search tells me that it is likely a configuration error.  According to the site below, it means the user trying to access does not have authorization to access that particular part of your localhost site.  More details needed.  It has nothing to do with rwx permissions.  What kind of file are you trying to access?
 
[https://www.freecodecamp.org/news/http-error-403-forbidden-what-it-means-and-how-to-fix-it/](https://www.freecodecamp.org/news/http-error-403-forbidden-what-it-means-and-how-to-fix-it/)

---

### Post by chat-4432 on 2022-06-16
> **yancek said:**
> I've not used docker or ngnix but a quick search tells me that it is likely a configuration error. According to the site below, it means the user trying to access does not have authorization to access that particular part of your localhost site. More details needed. It has nothing to do with rwx permissions. What kind of file are you trying to access?

[https://www.freecodecamp.org/news/http-error-403-forbidden-what-it-means-and-how-to-fix-it/](https://www.freecodecamp.org/news/http-error-403-forbidden-what-it-means-and-how-to-fix-it/)
[https://hub.docker.com/r/bgruening/galaxy-stable#Usage](https://hub.docker.com/r/bgruening/galaxy-stable#Usage)
how can i add my permissions to this ??

---

### Post by web-user on 2022-06-18
Try adding yourself to group docker using this command:
gpasswd -a yourname docker

---

