---
title: "Disk Permission"
date: 2007-03-15
forum: General Help
---

### Post by Kaphix on 2007-03-15
I searched around but nobody had the exact problem as me.

When I try writing files to my hard drive or file system, or basically anything other than desktop, it says:

Error while copying to "/media/disk".
You do not have permissions to write to this folder.

---

### Post by taurus on 2007-03-15
You need to be root, using sudo, if you want to write outside of your $HOME.  Therefore, use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Kaphix on 2007-03-15
How does that let me move files?

---

### Post by taurus on 2007-03-15
What file do you want to move and where do you want to move it to?

Applications -> Accessories -> Terminal
```
sudo cp **filename** **destination**
```

---

### Post by Kaphix on 2007-03-15
Sweet. Thanks.

---

### Post by Endolith on 2008-05-11
Ummm....  brute forcing it by using sudo isn't really a responsible solution, is it?  Shouldn't you be configuring the hard drive itself to have the correct permissions?

---

