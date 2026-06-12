---
title: "Argh!!! Wine screwed up my sources.list file! Help!"
date: 2008-01-14
forum: General Help
---

### Post by wookietim on 2008-01-14
So, thought I, "Wine would be fun to play with". So i went to the wine website and started to follow the steps to install it.

Immediately, I can no longer open my software manager. It says that sources.list is wrong. I looked and tracked the problem down to the first line in the Wine sources file. So, I figured that there would be no problem - I'll just comment it out.

BUT, Ubuntu tells me that i am not the owner of the file, so i can't make a change and save the file. So now, there is no way to change, delete, rename, or anythign else this file.... is there a simple fix?

---

### Post by shad0w_walker on 2008-01-14
use sudo to edit the file.

---

### Post by sumguy231 on 2008-01-14
When you edit it, you'll need admin priviledges since it's a system file. You can edit it this way:
```
gksu gedit /etc/apt/sources.list
```

---

### Post by wookietim on 2008-01-14
Thank you! That worked great!!!

You must remember - I am nowhere near a Linux guru yet. I know Windows quite well and I can use a Mac (sort of - although it's interface annoys me). I will have a lot of questions like this, so i hope i don't annoy everybody here...

---

### Post by ronmarley1 on 2008-01-14
> **wookietim said:**
> Thank you! That worked great!!!

You must remember - I am nowhere near a Linux guru yet. I know Windows quite well and I can use a Mac (sort of - although it's interface annoys me). I will have a lot of questions like this, so i hope i don't annoy everybody here...

You won't annoy anyone here.  Just ask your questions, and try to provide as much detail as possible.  
Welcome to Ubuntu!

---

