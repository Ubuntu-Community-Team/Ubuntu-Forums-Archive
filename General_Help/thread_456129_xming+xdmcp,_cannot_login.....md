---
title: "xming+xdmcp, cannot login...."
date: 2007-05-27
forum: General Help
---

### Post by thelost on 2007-05-27
OK, I wanted to use xming to log in from my windows machine to my ubuntu laptop. I want to compare it with VNC and see which is faster, and I just wanna be able to do it too!

I can get the GDM login screen up on xming just fine, but when I try to log in with the correct details it just stays on the login screen. It doesn't warn me that I've input incorrect details, just stays on the login screen.

Several questions:

1) What logs could I check to see what is going on when I try to log in over XDMCP?

2) What's wrong? Is there something obvious in the gnome.conf that I've missed?

---

### Post by gmconie on 2007-06-04
I am trying to get this working on 7.04. I found that it would not login remotely if the user was already logged in localy. Also had to re-boot after enabling remote login.

Currently I can log in but get a background with no options. There is another thread on this which appears unresolved at present.

---

