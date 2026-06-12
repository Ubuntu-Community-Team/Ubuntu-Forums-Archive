---
title: "Eclipse 3.2.1"
date: 2007-02-08
forum: General Help
---

### Post by floatleft on 2007-02-08
Hi,

This is a novice question: I need to unpack Eclipse 3.2.1 and put it into /usr/local (or possibly /opt), but I do not seem able to obtain the permissions to do this?  I tried logging in under Administration, but to no avail...

Could someone tell me how to do this or how to su to root?

Kind regards,
--
floatleft

---

### Post by ubu fubar on 2007-02-08
Why not just install it through Synaptic? Worked for me...

---

### Post by phossal on 2007-02-10
You just need to mv (move) it using the command line. You can unpack it anywhere, even your desktop, but then move the top folder (eclipse) to wherever you would like it to go. If I had eclipse on my desktop, and I wanted it in /usr/lib, I might do this:
```
sudo mv /home/phossal/Desktop/eclipse /usr/lib
```
Another common trick I use is to open Nautilus with root permissions so I can just cut and paste:
```
sudo nautilus
```

---

