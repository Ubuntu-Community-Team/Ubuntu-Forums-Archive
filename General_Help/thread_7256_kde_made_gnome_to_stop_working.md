---
title: "kde made gnome to stop working"
date: 2004-12-05
forum: General Help
---

### Post by snipes420 on 2004-12-05
I wanted to see how kde worked in ubunto.  bad idea. ](*,) 
I used apt-get to get the kde package and when i logged out to log in with kde, it didn't work. so I tried to log back in with gnome. that didnt work anymore either. has anybody any ideas about what could be wrong? i am writing this in the failsafe-terminal mode.

---

### Post by snipes420 on 2004-12-06
I figured it out

The owner of the .ICEauthority file in my users(snipes) home directory had been changed to root.
I used 

```
sudo chown snipes:snipes .ICEauthority 
```

in /home/snipes/ to fix it

---

