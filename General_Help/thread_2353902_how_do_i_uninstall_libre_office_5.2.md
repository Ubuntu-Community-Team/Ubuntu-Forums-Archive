---
title: "how do i uninstall libre office 5.2"
date: 2017-02-26
forum: General Help
---

### Post by Nailhac on 2017-02-26
I have just installed updated libre office with the much appreciated  help of this forum. I cannot find a method however to uninstal previous version 5.2 which keeps opening instead of newer version I cannot find the uninstall feature. I would appreciate advice. Many thanks.

---

### Post by RobGoss on 2017-02-26
Hello and welcome, 

Try running the following commands:

```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove 
```

This will remove Libreoffice completely and then you can do a fresh installation

---

### Post by Nailhac on 2017-02-26
Thanks RobGoss thats done it.

---

### Post by RobGoss on 2017-02-26
That's great glad I could help, if you have resolved your issue you can mark this thread as solved. You can use the **Thread tool **tab at the top of this post

Have a great day

---

