---
title: "grub error 17"
date: 2006-12-31
forum: General Help
---

### Post by brad1150 on 2006-12-31
ubuntu was running perfectly, i installed lots of multimedia and games and word processors,etc. . But today I was going to play an mp3, I have programs to play them, but when I opened th emp3, the computer just froze completely. afer 40 mins it was still int he sam estate so i hit the power button. When I turned it back on i got grub error 17. I am almost a complete noob at fixing ubuntu things. any help i sgreatly appreciated.

---

### Post by brad1150 on 2006-12-31
NVM, ill just do a complete reinstall. Another minus for ubuntu on my list.

It says the main filesystem is unknow, an d its the one linux was working for weeks on.

---

### Post by Sef on 2006-12-31
If you haven't reinstalled, then do this from the terminal (Applications > Accessories > Terminal):

```
sudo fdisk -l
```

and copy and paste the results here.  Likely one of your partitions got corrupted for some reason, but it can be fixed.

---

### Post by brad1150 on 2006-12-31
Too late, I already reinstalled it. There wasn't much on there i cant just redownload.\

now my problem is authentication failure for su

---

### Post by spockrock on 2006-12-31
su is not setup if I recall correctly on ubuntu, you have to use sudo.

---

