---
title: "need to get my graphics card drivers"
date: 2008-04-11
forum: General Help
---

### Post by valpobro on 2008-04-11
i have an ati radeon hd 2600 i tried to down load the drivers and install them but i got is what is on the picture so i tried to enable the POSIX shared memory by doing this 


    1. Add the following line to /etc/fstab (if it isn't there already): tmpfs /dev/shm tmpfs defaults 0 0
    2. Mount shared memory as follows: mount /dev/shm
    3. Issue the following command to check that it mounted properly: mount | grep "shm"

    If the mount was successful, then the following output (or similar) should appear:
    tmpfs on /dev/shm type tmpfs (rw)

after that i tried to install the drivers again but i just got the same thing

after changing the file do you just click save and then close it out or do you have to do somthing to save it?

---

### Post by phidia on 2008-04-11
The guides for ati cards are [here]("http://ubuntuforums.org/showthread.php?t=515573").
Hope that's helpful.

---

### Post by sm4n666 on 2008-04-11
download envy.....it will install it for you

---

