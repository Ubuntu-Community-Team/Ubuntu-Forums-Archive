---
title: "[SOLVED] How to change users primary group"
date: 2007-12-28
forum: General Help
---

### Post by uclalinux on 2007-12-28
Hi I can't figure this out, maybe someone can help me,

I made a newuser, 'jimmy' so under home directory it shows me 
```
drwxr-xr-x  2 jimmy  jimmy 4096 2007-12-28 11:53 jimmy
```

I am trying to change the group from jimmy to family. I want 
```
drwxr-xr-x  2 jimmy  family 4096 2007-12-28 11:53 jimmy
```
I tried using the 
```
usermod -g family jimmy
``` command, but it didn't work. 

Can someone tell me how to change the user jimmy group to family? 

Thanks

---

### Post by taurus on 2007-12-28
What is GUI (number) for group family in /etc/group?

```
cat /etc/group
```
Now, edit /etc/passwd

```
gksudo gedit /etc/passwd
```
and change GUI from probably 1001 or whatever the second number is to the number for family.  Save it and run

```
sudo chgrp -R family /home/jimmy
ls -la /home/jimmy
```
That's a dirty way to do it.

---

