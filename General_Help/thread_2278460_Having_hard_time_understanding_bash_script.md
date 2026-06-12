---
title: "Having hard time understanding bash script"
date: 2015-05-16
forum: General Help
---

### Post by jare2 on 2015-05-16
Hey guys! I need some help with understanding what exactly this script is trying to achieve. Its a snippet from a dockerfile  (ie run as root) 

```

  RUN mkdir -p /home/developer/workspace && \                                                                     
      echo "developer:x:1000:1000:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \ **# Why ",,,"  and "x" ???**
      echo "developer:x:1000:" >> /etc/group && \                                                                   
      mkdir -p /etc/sudoers.d && \                                                                                            
      echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \ **# make developer sudoer without password? ** 
      chmod 0440 /etc/sudoers.d/developer && \ **# Why?**
      chown developer:developer -R /home/developer && \                                                         
      mkdir -p /usr/bin/sudo && \ **# is it some kind of sudo shadowing? Why it might be needed?**
      chown root:root /usr/bin/sudo && chmod 4755 /usr/bin/sudo && \ **# ^^^**

```

---

### Post by SeijiSensei on 2015-05-16
```
mkdir -p /usr/bin/sudo
```
I don't where that script comes from, but this line is clearly bogus.  /usr/bin/sudo is a program file and exists already.  It's certainly not a directory.

What is the purpose of this script?  All it seems to do is create user called developer, then muck with things it shouldn't touch.  It uses some pretty dodgy techniques to do so like editing /etc/passwd directly.  You can create the user with "sudo adduser developer".  It's also pretty unlikely you'd want that user to have UID 1000.  That probably belongs to you, since it's the ID for the user created during installation.

Whoever wrote that script knows little or nothing about Ubuntu, or Linux for that matter.

---

### Post by jare2 on 2015-05-18
It's from here [https://github.com/fgrehm/docker-eclipse/blob/master/Dockerfile](https://github.com/fgrehm/docker-eclipse/blob/master/Dockerfile)  
Ubuntu docker image takes like 100-150mb so it might lack things like sudo.   Probably that is why the script is so hacky

---

### Post by SeijiSensei on 2015-05-18
This seems like a more straight-forward approach: [https://docs.docker.com/installation/ubuntulinux/](https://docs.docker.com/installation/ubuntulinux/)

---

