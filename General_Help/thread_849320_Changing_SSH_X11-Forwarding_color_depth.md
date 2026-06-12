---
title: "Changing SSH X11-Forwarding color depth"
date: 2008-07-04
forum: General Help
---

### Post by geforce123 on 2008-07-04
Hello All,

I'm setting up SSH x11-forwarding for users to use some app. on our app server.

I was wondering how to lower the color depth, the app is rather a bandwidth sucker.. (lot of graphics)

Please anyone ?

---

### Post by txcrackers on 2008-07-04
SSH doesn't know anything about the color-depth, sorry. What you *can* do is enable compression (see *man ssh*) - that might help, but then again it might not.

---

### Post by geforce123 on 2008-07-04
I wasn't sure whether ssh know or not the color-depth.

I did try the compression, but it's not helping...

Anyways, thanks, if someone else can give me pointers...

---

