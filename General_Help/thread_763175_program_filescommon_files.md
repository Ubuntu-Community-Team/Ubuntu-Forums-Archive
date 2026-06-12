---
title: "program files/common files"
date: 2008-04-22
forum: General Help
---

### Post by nasaJ81 on 2008-04-22
Im new to Ubuntu and am enjoying it very much..But am still learning alot. My question is is there an equivalent file on Ubuntu to windows program files folder and common files folders. On windows sometimes you download a program and even after you delete it and remove it still keeps random folder usually in one of these places. Is there such folders in Ubuntu and if so how do i get there. Thanks you---new user

---

### Post by Lokine on 2008-04-22
In your home folder, there should be a folder called "Public". That's the one.

EDIT: Oops, my mistake, I misunderstood the question.

---

### Post by Diabolis on 2008-04-22
The structure of how files are stored in linux is very different. While windows stores all the programs in one folder, linux does not have that folder. A program may not even be stored in just one folder. The way linux is designed is to eliminate redundancy, so if you have 2 applications that use the same library. Then the library will be stored in the folder "libs" and the applications will be (just an example) in the folder "etc".

Applications take what they need from different folders. Just google for linux/ubuntu structure. Structures may change from ubuntu to other distros also. This is a short description: [http://www.edumax.com/linux-basics-linux-typical-directory-structure.html](http://www.edumax.com/linux-basics-linux-typical-directory-structure.html)

You can see all the applications that you have installed in synaptic package manager, it is located in System / administration.

> In your home folder, there should be a folder called "Public". That's the one.
I have never seen that folder, do you have it?

---

### Post by louieb on 2008-04-22
Short version [Filesystem Hierarchy Standard - Wikipedia]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
Long version [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

Long version goes into greater detail about what goes where and why.

---

