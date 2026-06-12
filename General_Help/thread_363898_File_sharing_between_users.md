---
title: "File sharing between users"
date: 2007-02-17
forum: General Help
---

### Post by Foxmike on 2007-02-17
This is just a very simple question.  I have a partition that carries out all the multimedia stuff on the computer.   It is mounted as *"/media/multimedia/"* owned by *"root:users"* and has access permission for read/write for owner and group*.  Both me and my wife are in group *"users"*.

Now, what I would like to do is:
- when I or my wife add stuff to that partition, the added stuff get the parent's directory owner/group values as well as permissions so the other one will have automatic access to what has been putted into the partition.  Is that possible?
- We both use F-Spot to manage pictures.  Pictures are shared between my wife and I.  Is there a way to update all collections when new stuff has been added to a specific directory?

I'm pretty sure there is an easy answer, but I just haven't found it yet...

Thank you in advance for your help!

- FM

---

### Post by kidders on 2007-02-17
Hi there,

> **Foxmike said:**
> I'm pretty sure there is an easy answer, but I just haven't found it yet...The answer *is* easy, but could be quite tricky to find, if you don't know what to look for! I think what you want to do is set the shared directory's SGID bit (with **chmod**). That would force the directory's group ownership on newly created files, regardless of who put them there.

Take a look at these: [http://www.google.com/search?hl=en&rls=en&q=suid+sgid](http://www.google.com/search?hl=en&rls=en&q=suid+sgid).

Another alternative would be to switch your (and your wife's) primary group to "users", rather than your private groups (the default). Doing that would have all sorts of knock-on effects though, so might not be such a smart idea.

---

### Post by Foxmike on 2007-02-18
Thank you very much!  That was exactly what I was looking for!  Actually, I guess it will be cleaner (and thus easier) to go with option 1.

Thanks again!

- FM

---

