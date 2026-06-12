---
title: "X window not found?? Scilab related"
date: 2006-07-13
forum: General Help
---

### Post by slimdog360 on 2006-07-13
Okay so this is related to my other thread [here]("http://www.ubuntuforums.org/showthread.php?t=214792")
but Ive had no luck in a response so Im going to try something else.
I want to compile Scilab from source but when I try ./configure I get this error ```
configure: error: X Window not found
```
Can anyone help me to fixing this.
thanks

---

### Post by slimdog360 on 2006-07-13
bump, I cant find an answer anywhere. there are a lot of references to windows.

---

### Post by paulmilliken on 2007-06-11
> **slimdog360 said:**
> bump, I cant find an answer anywhere. there are a lot of references to windows.

You are missing some files.  To install the missing files type "sudo apt-get install xlibs-dev"

You will also need to install "tk-dev" and "tcl8.4-dev" to compile scilab.

Paul

---

