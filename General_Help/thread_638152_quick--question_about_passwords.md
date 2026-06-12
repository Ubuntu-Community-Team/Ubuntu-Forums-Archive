---
title: "quick--question about passwords"
date: 2007-12-11
forum: General Help
---

### Post by mD3m4r415 on 2007-12-11
Hello, is there a way to make a password under 6 characters long?  every time i try to make one it says it must be 6... i want one to be 4.  is there a file i can modify??

---

### Post by drs305 on 2007-12-11
What app does the password belong to. My ubuntu login password was once only 4 characters until I changed it.

---

### Post by geirha on 2007-12-11
/etc/logn.defs should be the file to edit. However, root is allowed to set any password, so instead of typing "passwd", try with "sudo passwd $USER"

---

### Post by mD3m4r415 on 2007-12-11
k thanks im gonna try that... im assuming "$USER" is the username of the person whose password is being changed.

---

### Post by mD3m4r415 on 2007-12-11
thanks it works!

---

