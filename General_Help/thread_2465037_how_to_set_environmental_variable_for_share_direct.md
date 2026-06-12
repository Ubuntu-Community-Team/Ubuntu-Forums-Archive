---
title: "how to set environmental variable for share directory"
date: 2021-07-20
forum: General Help
---

### Post by monkeybrain20122 on 2021-07-20
I would like to install a game locally instead of installing into /usr or /usr/local since I don't like to litter the file system with pieces that I can't keep track of. Now I can use the PATH and LD_LIBRARY_PATH override /usr/bin and /usr/lib etc but the program looks for resources in /usr/share, is there an environmental variable to set the share directory?

Thanks.

---

### Post by vanadium on 2021-07-20
"/usr/local" would be a good place to install apps you compile yourself or install in another way outside of the APT package manage. In Ubuntu, it is by default setup in your PATH to override /usr/bin. Why is it a problem is the program looks for resources in /usr/share? There is a /usr/local/share directory where you can place your custom resources, icons, etc., which, again, will take precedence over /usr/share.

---

### Post by TheFu on 2021-07-20
Well, seems the forum is still broke. Hopefully, someone will let Canonical know the link so they can see why it is rejected as a post.
My reply is here: [http://s](http://s) p r u n g e . u s/Crue6u

---

