---
title: "how do I set an alternate root password"
date: 2007-03-25
forum: General Help
---

### Post by donkyhotay on 2007-03-25
I don't like having SUDO use the same password I use to login. I do like how I can use it to prevent logging on to my system with username root though. Is there any way to configure sudo to only grant access with a different password besides a users login password? I've been reading the documentation on sudo but haven't seen anyway of doing this.

---

### Post by smokey edgy on 2007-03-26
sudo passwd

It will prompt you for a password (which will become your root password).

---

### Post by donkyhotay on 2007-03-26
I know how to add a root password that will allow me to login as root but that isn't what I'm trying to do. I want a second password that sudo  will accept for granting root access without allowing logging in directly as root (or su) which simply adding a root password would do.

---

### Post by smokey edgy on 2007-03-26
Sorry about that, misread your post.

---

