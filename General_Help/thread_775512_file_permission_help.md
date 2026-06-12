---
title: "file permission help"
date: 2008-04-30
forum: General Help
---

### Post by mzruya on 2008-04-30
Hello, i want to create a a public folder for users to be able to add content to, but i don't want any user to have to ability to change the other user's files...

i read the manuals but still didn't manage,
what is the proper permission settings for this kind of scenario ?

---

### Post by lightblue on 2008-04-30
right click in a folder then go to properties.
There you will see a tag named Permission's

From there you can choose what can any user do will the selected folder.

user  = the owner of the folder can not be changed from here
group = here you can choose what permission's each member of a group will have (there is a graphic tool in system administration named users and groups where you can manage group's  )
other's = here you specify the permissions for everyone else


for the tabs folder access and file access they do what their name are 

I hope i helped

---

### Post by mzruya on 2008-04-30
this configuration allows one user to alter another user's files
how do i make sure one doesn't delete the other's files ?


thanks..

---

### Post by kpkeerthi on 2008-04-30
You need turn on sticky bit on the shared folder so a user can delete or rename the files that he/she owns.

[More Info]("http://www.google.co.in/search?q=unix%2Csticky+bit") :)

---

### Post by mzruya on 2008-04-30
> **kpkeerthi said:**
> You need turn on sticky bit on the shared folder so a user can delete or rename the files that he/she owns.

[More Info]("http://www.google.co.in/search?q=unix%2Csticky+bit") :)

thanks ! helped alot...

---

