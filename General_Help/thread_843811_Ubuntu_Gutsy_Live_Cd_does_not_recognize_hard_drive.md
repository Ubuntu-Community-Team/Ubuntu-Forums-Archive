---
title: "Ubuntu Gutsy Live Cd does not recognize hard drives?!"
date: 2008-06-28
forum: General Help
---

### Post by morbid_bean on 2008-06-28
I have been using Ubuntu hardy for about  a month now and with the popular random lock-ups I and many others experience is getting old so i decide ill go with an older version of ubuntu....after a long live cd load I only find that my 2 Ide hard drives are not detected...i found that out by when trying to install 7.10 nothing shows up on the partition list....so i look under places list and nothing is there...

---

### Post by morbid_bean on 2008-06-28
bump

---

### Post by morbid_bean on 2008-06-28
ok so i resort to hardy xubuntu and it cant detect my slave drive..but only the master....:confused:

---

### Post by morbid_bean on 2008-06-29
bump :(

---

### Post by VMC on 2008-06-29
Boot from livecd and type from Terminal :
```
sudo fdisk -l
```

Also are your hard drives cabled off of one cable. One master and the other slaved?
Right now without seeing the output, I'm guessing you have two hard drives.

---

