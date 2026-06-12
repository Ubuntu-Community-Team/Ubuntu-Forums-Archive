---
title: "Changing permissioins not working"
date: 2007-09-11
forum: General Help
---

### Post by s-lime on 2007-09-11
I logged in as root (unsecure :D)... Then i selected all files and folders and changed permission that everyone can write.

Then I logged in as normal user and I still couldn't write.

What's wrong?

---

### Post by southernman on 2007-09-11
Insecure

---

### Post by tszanon on 2007-09-11
> **s-lime said:**
> I logged in as root (unsecure :D)... Then i selected all files and folders and changed permission that everyone can write.

Then I logged in as normal user and I still couldn't write.

What's wrong?
I think you changes only the permissions of the files you selected. I mean, going to Nautilus, selecting everything under / and setting full access to anyone would not change the permissions on the files/folders inside /home, for example.

I think you should do this:
```
cd /
sudo chmod 777 -R *
```
But take care, because this is NOT RECOMMENDED, due to security reasons.

---

### Post by s-lime on 2007-09-11
Thaks for help.

Error:
chmod: cannot access `rok:rok': No such file or directory

what would be a query if I would like to set unlimited permissions to 'rok' for whole filesystem?

---

### Post by southernman on 2007-09-11
Insecure

---

### Post by s-lime on 2007-09-11
sudo chmod -R 777 rok:rok /

---

### Post by southernman on 2007-09-11
WHAT... you want to open up your / partition?

Just say NO!

You may as well just log in as root and completely bork your system... or better yet, let someone else do it for you.

---

### Post by s-lime on 2007-09-11
I just want to set all files for control to 'rok'. Rok is in root group.

Currently rok has only read permissions.

---

### Post by southernman on 2007-09-11
It's done that way so you don't accidentally bork your system to where you have to reinstall... or worse spend hours on end trying to fix it.

If you need to edit a system file (owned by root), fgs just use sudo. It may be a slight inconvience at the time, but the headaches it could save you are not measurable.

Users are in the root group so that you can use sudo.

Please, take the advice to heart... or know that if you don't, you've been warned.

---

### Post by s-lime on 2007-09-11
Thanks.

---

