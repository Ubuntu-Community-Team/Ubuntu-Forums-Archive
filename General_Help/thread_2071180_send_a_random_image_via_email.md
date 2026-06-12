---
title: "send a random image via email"
date: 2012-10-14
forum: General Help
---

### Post by sohlinux on 2012-10-14
How can I send a random image from a folder and any of its subfolders

the name of the file could be anything.jpg

something like the following but to take a random image from /images/folder and any of the subfolders

mutt -s "image of the day" [email]my@mail.com[/email] -a /images/image1.jpg < mailmessage.txt

thanks

---

### Post by Vaphell on 2012-10-14
maybe something like

```
mutt -s "image of the day" [email]my@mail.com[/email] -a "$( find /images -type f | sort -R | head -1 )" < mailmessage.txt
```

---

### Post by sohlinux on 2012-10-15
> **Vaphell said:**
> maybe something like

```
mutt -s "image of the day" [email]my@mail.com[/email] -a "$( find /images -type f | sort -R | head -1 )" < mailmessage.txt
```

perfect, but if other file types exist I dont want to include those, only images .jpg or JPG 

thanks

---

### Post by Vaphell on 2012-10-15
find /images -iname '*.jpg' -type f

---

### Post by sohlinux on 2012-10-15
> **Vaphell said:**
> find /images -iname '*.jpg' -type f

thanks

---

