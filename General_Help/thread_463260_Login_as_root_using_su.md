---
title: "Login as root using su"
date: 2007-06-03
forum: General Help
---

### Post by Cool Surfer on 2007-06-03
How do I login as root using terminal pl.

I tried su n sudo , but on pwd, ir says wrong pwd.
I have onlyone pwd.

---

### Post by Cool Surfer on 2007-06-03
"I am getting authentication failure, sorry"
Any  help pl.

---

### Post by pseudonym on 2007-06-03
sudo -s -H will change you to root user. but for most things admin-related you should be fine just using sudo, and staying as your user.

---

### Post by misfitpierce on 2007-06-03
Yeah su does not work on ubuntu for me, it worked fine in Mandriva. So im guessing different way of doing things.

---

### Post by Cool Surfer on 2007-06-03
> **pseudonym said:**
> sudo -s -H will change you to root user. but for most things admin-related you should be fine just using sudo, and staying as your user.


Thanks. It worked. 

You guys are great!! :)

---

### Post by gerscht on 2007-06-03
```

sudo su
Password:

```
works flawless,
but as it has been said in the post before, sudo will do for most admin tasks

---

### Post by RedSquirrel on 2007-06-03
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

