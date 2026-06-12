---
title: "Missing Ubuntu usplash"
date: 2008-06-01
forum: General Help
---

### Post by toucher5 on 2008-06-01
I have ubuntu on my desktop at home and it works fine except when its loading and is supposed to show the usplash it just goes black. can anyone tell me how to get this back? 

my kernel line on grub has this, ro quiet splash, at the end of it which is supposed to show the usplash.

any help is appreciated.

:popcorn:

---

### Post by ajgreeny on 2008-06-01
Are you fully updated to the 2.6.24-17 kernel, as this seems to do the trick in some cases, don't know why, but it seems so.

---

### Post by toucher5 on 2008-06-01
yes. I installed with the 7.10 disk and the two weeks after 8.04 was released I updated. (I don't have internet at home. I bring the desktop over to my mother-in-law's house for updates).

---

### Post by SirPerigrin on 2008-06-01
try reconfiguring usplash

> sudo dpkg-reconfigure usplash


---

