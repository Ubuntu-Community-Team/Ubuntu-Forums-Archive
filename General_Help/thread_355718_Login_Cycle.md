---
title: "Login Cycle"
date: 2007-02-07
forum: General Help
---

### Post by taekwondodogoof on 2007-02-07
Hi,
       I'm having a wierd problem. I logged into Ubuntu one day fine.. and a little popup in the lower right hander corner said "99% of disk space used". The computer then froze.. and I couldn't get into terminal or anything.
       I restarted.. and the login screen popped up. I logged in.. then the Nvidia driver splash appeared.. then a black screen with a blinking text block appeared.. and the login screen came back. I can get into recovery mode fine.
            Thanks for the help :)

---

### Post by taurus on 2007-02-07
Sounds like you are running out of disk space.  Boot into recovery mode and run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
(replace **username** with the actual login name for your machine...)
df -h
```

---

### Post by taekwondodogoof on 2007-02-07
Thanks for the help =D! That fixed it.. I'm going to clear out a few space-filling apps so it doesn't happen again!

---

