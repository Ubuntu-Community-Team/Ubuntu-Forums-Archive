---
title: "Still no flash in firefox!!"
date: 2007-12-21
forum: General Help
---

### Post by alexv305 on 2007-12-21
I took off my 64 bit Ubuntu 7.10 and installed the 32 bit. After installing the flashplugin-nonfree I still have no flash... Why can't I get it to work?

Does anyone know why its not working?

---

### Post by Skweek on 2007-12-21
I had the same problem you had,  and fixed it by downloading the flash plugin from Macromedia and running the intall script that came with it.

Be sure to specify "/usr/bin/firefox" when it asks you for the browser location.

---

### Post by shifty2 on 2007-12-21
I had the same issue. Solved it by following the instructions at this link (talks you through the proccess suggested above): [http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

---

### Post by fain on 2007-12-21
You probably suffer from this [bug]("https://bugs.launchpad.net/ubuntu/feisty/+source/flashplugin-nonfree/+bug/173890") 

If you scroll down some one built a package for amd64 gutsy that mostly fixes the problem.

---

### Post by ilrudie on 2007-12-21
Works like a charm except the directory is /usr/lib/firefox.  Thanks

---

