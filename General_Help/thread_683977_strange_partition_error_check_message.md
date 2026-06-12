---
title: "strange partition error check message"
date: 2008-01-31
forum: General Help
---

### Post by rabid9797 on 2008-01-31
recently during boot up ive started getting this message

[img]http://xs223.xs.to/xs223/08054/01-31-08_1607196.jpg[/img]

sda1 is my main partition(ubuntu), so it shouldn't be taking that long...(only 70GB) but the error message is even stranger. can anyone help me troubleshoot what this means?

oh, forgot to add, it takes almost 2 minutes to check the entire partition. it mounts correctly and with all permissions after that(during actual use), and i get no other errors.

---

### Post by rabid9797 on 2008-02-01
bump..

---

### Post by pointone on 2008-02-01
They're not fsck problems; it's Ubuntu trying to do something with your USB devices in the background. Check those connections.

Post the output of:

```
sudo lsusb -v -s 5:1
```

---

