---
title: "How to set environment variables??"
date: 2006-07-02
forum: General Help
---

### Post by AlliumPorrum on 2006-07-02
I'd like to change the PATH variable a bit, and add a JAVA_HOME- system variable, but I just can't find out how to do it?? And I don't mean to do this just for the current session, but for the rest of my life...;)  How should I do it??

---

### Post by ato on 2006-07-02
```
sudo gedit /etc/environment
```

;)

---

### Post by AlliumPorrum on 2006-07-02
Well that was easy, when you know how to do it. Thanks!

---

### Post by soze on 2006-07-02
[QUOTE=ato]```
sudo gedit /etc/environment
```

;)[/QUOTE]

That will affect the environment for all users. For these purposes, it might be better to edit ~/.bashrc for the particular user.

---

### Post by no1wantdthisname on 2006-07-02
Editing the /etc/environment changes the PATH for all users.
Editing .bashrc will only affect terminals, so the run dialog won't be affected by the PATH change. 

If you're using gnome you can just edit the .gnomerc file that starts when you use gnome from gdm.  
Just create a ~/.gnomerc, chmod +x it, and put something like this:
```
#!/bin/sh
export PATH=$HOME/bin:$PATH
```

---

