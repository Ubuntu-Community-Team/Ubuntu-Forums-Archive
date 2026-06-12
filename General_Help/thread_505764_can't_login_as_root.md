---
title: "can't login as root"
date: 2007-07-20
forum: General Help
---

### Post by joereith on 2007-07-20
my comp won't let me login as root what can i do?

---

### Post by distroman on 2007-07-20
```
sudo -i
```
Is that what your looking for?

---

### Post by joereith on 2007-07-20
i am trying to log on to my comp as root to delete some locked files

---

### Post by sisco311 on 2007-07-20
by default , the root account is locked in ubuntu.
please read [this ]("https://help.ubuntu.com/community/RootSudo")

---

### Post by joereith on 2007-07-21
i can't delete a file that is in my trash. it says i don't have the permissions to do it and i'm not using the command prompt, i clicked empty trash and i got that message

---

### Post by por100pre1 on 2007-07-21
```
sudo rm -r <fileorfoldername>
```

Be careful using this command!!!

---

### Post by joereith on 2007-07-21
says it can't remove it it's a directory

---

### Post by distroman on 2007-07-21
```
sudo rm -rf /home/username/.Trash
```
Change username with your username.

---

### Post by joereith on 2007-07-21
that worked but my taskbar trash icon still says 1 item in trash but when i open it  it's empty

---

