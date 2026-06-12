---
title: "Cant find libGLEW"
date: 2017-11-20
forum: General Help
---

### Post by jayecrow on 2017-11-20
Hi I have moved to Artful Kubuntu and am trying to symlink libGLEW for an application. Tho I cant seem to find it, I dont have a lib64 directory and theres no libGLW in /usr/lib/

Where is it ?

Thankyou

---

### Post by Holger_Gehrke on 2017-11-20
why don't you tell your computer to find it for you ?
```

find /lib /usr/lib /usr/local/lib -name libGL*
```
Would check the usual directories and their subdirectories for any file whose name starts with "libGL".  On my system libGLEW.so.2.0.0 is found in '/usr/lib/x86_64-linux-gnu/'.

Holger

---

### Post by jayecrow on 2017-11-20
Thankyou so much, I have been on windows for a while and have forgotten some things. Problem solved.
:)

---

### Post by vasa1 on 2017-11-20
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jayecrow on 2017-11-20
done

---

