---
title: "Vim color (comments have 2 different colors)"
date: 2012-10-24
forum: General Help
---

### Post by scufkanc on 2012-10-24
Hello folks.

I have VIM installed on a server x32 edition of Ubuntu 10 (installed yesterday). The colorcode on the image below worries me. Why are the comments od different color than other comments after I spell the word **"disallow"** or **"allow"** correctly?



[IMG]http://i3.photobucket.com/albums/y62/cegu/vimubuntu_zps185c4d71.png[/IMG]

---

### Post by drmrgd on 2012-10-24
Because it's reading 'disallow' or 'allow' as a function or parameter that takes an argument.  So, it's recognized and color coded accordingly.  When you misspell it, it's not recognized as the correct function / parameter and not color coded correctly.  It's helpful in telling you that you misspelled it.

---

### Post by scufkanc on 2012-10-25
The top one is the one that is correct, the bottom one is incorrect. Why would the word "allow" be any different than let's say "secret"?

---

