---
title: "warning boot volume low free up disk space"
date: 2015-02-09
forum: General Help
---

### Post by Bushcraft Bill on 2015-02-09
it is saying their is little space remaining in "boot" I tried gparted to make boot bigger but it does not let me do anything so what do I use to fix this problem?
it tells me to remove unused programs or files but can I move files out of boot? dont want to bugger things up by doing that would that be safe to do?

using windows 8 and ubuntu 14.04 and duel booting setup...

---

### Post by slickymaster on 2015-02-09
See this: [How do I free up more space in /boot?]("http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot")

---

### Post by mörgæs on 2015-02-09
```
sudo apt-get autoremove
```

---

