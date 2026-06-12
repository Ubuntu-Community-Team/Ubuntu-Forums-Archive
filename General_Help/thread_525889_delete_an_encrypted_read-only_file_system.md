---
title: "delete an encrypted read-only file system"
date: 2007-08-14
forum: General Help
---

### Post by laurax17 on 2007-08-14
please help! delete an encrypted read-only file system. Discuss please help! delete an encrypted read-only file system, on the Ubuntu Help forum of LinuxForums.org, where people come to for Linux help.

---

### Post by aldenhg on 2007-08-14
You should be able to use GParted to do that. To get Gparted, open an terminal and type ```
sudo apt-get install gparted
```
Put in your password, hit enter and wait for it to install. Once it's installed, run the command ```
gksudo gparted
```
Find the partition that you want to delete and then right click on it, unmount it if it's mounted and then delete it. 
Make sure that you actually want to delete the partition before you do it. Anything on it will be gone forever, so think carefully before you do anything rash.

---

### Post by laurax17 on 2007-08-14
thank you thank you thank you!!!!

you've absolutely made my night! my life

thank you for helping posters!

---

### Post by HermanAB on 2007-08-14
To delete an encrypted file system, all you need to do is forget the key.

---

