---
title: "Log in screen won't go away"
date: 2007-07-15
forum: General Help
---

### Post by zweiundzwei on 2007-07-15
I just reinstalled Dapper. Every time I try to log in a brown screen appears for a second or so and then I get the log in screen again, asking me to enter my username and password. This way, I am not able to use Ubuntu at all.

A workaround is to delete the right screen resolution from the xorg.conf file and  using only 1024x786, but that obviously is no permant solution.

---

### Post by bapoumba on 2007-07-15
Would you be running out of disk space?
From the login screen, hit <CTRL-ALT-F2>, login, and run:
```
df -H
```

You can make some room in your root (/) partition with:
```
sudo aptitude clean
```
Look also in your /home partition for files to delete.

Go back to the GDM login screen with <CTRL-ALT-F7>

---

### Post by zweiundzwei on 2007-07-15
That doesn't seem to be the problem. On every partition there's about 10GB of free space and df -H tells me I'm using at most 8% of all space.

---

### Post by bapoumba on 2007-07-15
Hmm, ok. What video card do you have, and what video drivers are you using? Any desktop effects?

---

### Post by zweiundzwei on 2007-07-15
My video card is Nvidia GeForce 6100 and I'm using the vesa driver.

I had the same problem I have now before with Feisty too (but with my first Dapper installation I didn't), and had tried using the real nvidia driver then, but that didn't help.

---

