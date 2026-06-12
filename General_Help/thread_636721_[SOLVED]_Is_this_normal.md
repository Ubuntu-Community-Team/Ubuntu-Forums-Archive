---
title: "[SOLVED] Is this normal?"
date: 2007-12-10
forum: General Help
---

### Post by idiot1000 on 2007-12-10
I installed Ubuntu again a few minutes ago with an existing home install the user account on the home install was Anonymous right...

Now my plan was to make a new user called nerd and move Anonymous's files from his home dir to nerds desktop and that would be all...

Because I don't really know how this works and I hated the thought that if I made another user called Anonymous his home dir might be erased with the new one. so..

I did that it worked fine but then I figured out I could get most of my old settings if I made a new account call anonymous and used his already exisiting home dir

(which I should have just done in the install but I am an idiot remember)

then I decided to move the files back to Anonymous' directory from Anoymous but I didn't have the permishions so I chowned it folder: chown -hR anonymous /home/nerd (or some thing like that) and I moved the files from nerds desktop back to anonymous'

I was then going to delete the nerd account but now it doesn't even exist it's hell glichy.

[http://img442.imageshack.us/img442/4025/screenshotyu6.png](http://img442.imageshack.us/img442/4025/screenshotyu6.png)

Look above?

This isn't really urgent I am just never going to touch anything again :lolflag:

Can this be fixed?

---

### Post by CatKiller on 2007-12-10
From **man users**:

>        users  -  print the user names of users currently logged in to the cur&#8208;
       rent host It doesn't do what you think it does.

---

### Post by mali2297 on 2007-12-10
> **idiot1000 said:**
> 
I was then going to delete the nerd account but now it doesn't even exist it's hell glichy.

[http://img442.imageshack.us/img442/4025/screenshotyu6.png](http://img442.imageshack.us/img442/4025/screenshotyu6.png)

Look above?


The output seems normal, from the man page:
> 
users - print the user names of users **currently logged in** to the current host

That the same user is listed multiple times is also normal, it depends on how many shells you are running.

To delete the nerd account, I think this would work:
```

sudo deluser --remove-home nerd

```
:!: Use at own risk, look in **man deluser** to be better informed.

---

### Post by erfahren on 2007-12-10
I think it is. mine lists me twice as well. I looked into something similar to that recently when running "uptime" - it shows 2 users as well.

I found this thread concerning it: [http://forums.macosxhints.com/archive/index.php/t-52598.html](http://forums.macosxhints.com/archive/index.php/t-52598.html)

---

### Post by idiot1000 on 2007-12-10
Ok thanks guys

---

### Post by nikoPSK on 2007-12-11
please mark this thread as "SOLVED". :D

---

