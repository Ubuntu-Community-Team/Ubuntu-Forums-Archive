---
title: "Cant login into GNOME"
date: 2006-12-08
forum: General Help
---

### Post by cazz on 2006-12-08
Hi
When I try today to login into my ubuntu it say username and I write right username and after it ask the password and I write the right password but nothing happen
it load the login screen again.

When I have write the username and the password again it show again the login screen.

---

### Post by bapoumba on 2006-12-08
Please go to one of the tty sessions (ALT + F2 for ex.), login and psw, and check if your partitions are full, specially /home and /var)
```
df -h
```
You might have to do a little clean up in our /home directory ;)
```
sudo apt-get clean
```
should also free some space in your root directory.

---

### Post by cazz on 2006-12-08
thanks it work :D

---

### Post by bapoumba on 2006-12-08
Welcome :)

---

