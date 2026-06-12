---
title: "Boot issues"
date: 2007-06-02
forum: General Help
---

### Post by nextbgates95 on 2007-06-02
I am having some of the same issues other people are having with the boot not being able to complete and being dropped to a shell.  Both times I have had to Hard Boot because Ubuntu froze.  I would just like to know how to shut down if Ubuntu is unresponsive without corrupting my virtual disk image.  Thanks

--
Jay

---

### Post by ago on 2007-06-02
You can usually press ctrl+alt+f2 to get a shell and kill any offending program with pkill
If the keyboard does not respond see [http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html](http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html) 

Try to avoid hard booting wubi, since it uses a nested filesystem and that makes it far more vulnerable than using either ext3 or ntfs by themeselves.

---

### Post by nextbgates95 on 2007-06-02
Thanks!  I was trying ctrl+alt+backspace  but i forgot to try ctrl+alt+F2.:oops:  And I never knew about sysRq.  I always thought it was just a key. :)  I was afraid I wasn't going to be able to get back into Windows, but my PC seems to perform miracles.

--
Jay

---

