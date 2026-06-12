---
title: "file problem"
date: 2008-06-18
forum: General Help
---

### Post by Orfeus on 2008-06-18
something weird is going on with ubuntu. I have files stored in Desktop but i can only see them from terminal. If i go to the directory they are not there. IS there something wrong with the permissions?

thanks

---

### Post by Rocket2DMn on 2008-06-18
Can you please tell us what files they are?  If they start with a . then they are hidden files.  If they end with a ~ then they are temp files that can be deleted.
Hit CTRL+H to show them on your Desktop.

---

### Post by Orfeus on 2008-06-21
i know that and they are not hidden. Both of them should be visible

---

### Post by Rocket2DMn on 2008-06-21
Can you please change directory in terminal to the correct folder and post
```
ls -l
ls -al
```
Then post screenshots of the desktop itself and ~/Desktop folder in nautilus.

---

### Post by VMC on 2008-06-21
I've had that happen before. From Desktop, if you push the "refresh button", F5, then they magically appear.

---

