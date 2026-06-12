---
title: "How do I set user home directory from the command line?"
date: 2007-08-24
forum: General Help
---

### Post by Jongi on 2007-08-24
Say the user is called user and the directory I want to set as the home directory is /home/jongi

---

### Post by bernied on 2007-08-24
```
sudo cp /etc/passwd /etc/passwd.bak
sudo nano /etc/passwd
```
Then find the entry for user, and change where it says /home/user to /home/jongi
Then log out, and back in again.

But beware, there are files in the original home directory that you might need. When it all gets too much, restore to sanity with
```
sudo cp /etc/passwd.bak /etc/passwd
```

Why are you doing this? It sounds a bit mad to me.

---

