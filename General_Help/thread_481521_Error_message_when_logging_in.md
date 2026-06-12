---
title: "Error message when logging in"
date: 2007-06-22
forum: General Help
---

### Post by nami on 2007-06-22
Anyone know why I am getting this error message after typing in the password and pressing enter?  When I click OK it lets me in.

[[IMG]http://img394.imageshack.us/img394/2958/dsc02208ly6.th.jpg[/IMG]](http://img394.imageshack.us/img394/2958/dsc02208ly6.jpg)

---

### Post by NeoLithium on 2007-06-22
When you log into your computer, you should open up a terminal window, and type:
```

sudo chown YOUR_USERNAME:YOUR_USERNAME /home/YOUR_USERNAME

```
It seems as though your /home directory was chowned to some other user. Then log out and back in, and you should be good.  Make sure you don't miss the : between your two usernames before the directory :)

---

### Post by nami on 2007-06-24
I tried that and it didn't seem to make a difference

here is the output from ls -l

> nami@nami-desktop:/home$ ls -l
total 8
drwxrwx--x 44 nami  nami  4096 2007-06-24 10:15 nami
nami@nami-desktop:/home$ 


---

### Post by nami on 2007-07-05
*bump*

---

