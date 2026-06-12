---
title: "How to make gnump3d start on bootup?"
date: 2007-05-03
forum: General Help
---

### Post by tgoose on 2007-05-03
I installed gnump3d months ago on Edgy, and since then I've had no luck with it starting up automatically. It's fine running /etc/init.d/gnump3d start , but I'm sure I shouldn't have to do this every time for a server. I'm sure it's pretty simple but I don't know how to sort this out. If I remember correctly, it just worked on Fedora Core and, with a bit of fiddling, on Windows. Any help would be much appreciated. Thanks.

---

### Post by xxzeenoxx on 2007-07-10
> **tgoose said:**
> I installed gnump3d months ago on Edgy, and since then I've had no luck with it starting up automatically. It's fine running /etc/init.d/gnump3d start , but I'm sure I shouldn't have to do this every time for a server. I'm sure it's pretty simple but I don't know how to sort this out. If I remember correctly, it just worked on Fedora Core and, with a bit of fiddling, on Windows. Any help would be much appreciated. Thanks.

Were you ever able to figure out how to run the command at startup?

---

### Post by tgoose on 2007-07-10
I managed to work out how to get it to start up on login, which is just as good for a single user computer like mine. It's as simple as going to System -> Preferences -> Sessions, and adding a New one with the command ```
/etc/init.d/gnump3d start
```!

---

