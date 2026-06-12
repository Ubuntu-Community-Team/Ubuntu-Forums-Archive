---
title: "[SOLVED] How to log in as root?"
date: 2008-06-14
forum: General Help
---

### Post by mahela007 on 2008-06-14
I have installed SAMBA and before i added myself as a user I added a sharing folder. (I'm a newbie to networking).
Now I have added myself as a user and the nedtworking aprt of it is going fine but I also want to delete the folder I added by accident.
I tried doing this in Nautilus but it says the owner of the folder is root and that I cannot delete it. How do I delete this folder? If I have to log in a root, can someone tell me how to do it?

---

### Post by sujoy on 2008-06-14
> **mahela007 said:**
> I have installed SAMBA and before i added myself as a user I added a sharing folder. (I'm a newbie to networking).
Now I have added myself as a user and the nedtworking aprt of it is going fine but I also want to delete the folder I added by accident.
I tried doing this in Nautilus but it says the owner of the folder is root and that I cannot delete it. How do I delete this folder? If I have to log in a root, can someone tell me how to do it?

open nautilus with root permission, alt+f2 and type gksudo nautilus or open a terminal and type sudo nautilus.

---

### Post by f4k1r on 2008-06-14
> **mahela007 said:**
> I have installed SAMBA and before i added myself as a user I added a sharing folder. (I'm a newbie to networking).
Now I have added myself as a user and the nedtworking aprt of it is going fine but I also want to delete the folder I added by accident.
I tried doing this in Nautilus but it says the owner of the folder is root and that I cannot delete it. How do I delete this folder? If I have to log in a root, can someone tell me how to do it?

u want to remove it from sharing or want to delete it permanently from HD??
if u wan to delete it permanently sudo rm -r /path to the directory

---

### Post by Rocket2DMn on 2008-06-14
Here are some links that may interest you:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
If you have any questions regarding those pages, please ask!

---

### Post by Sef on 2008-06-14
> open nautilus with root permission, alt+f2 and type gksudo nautilus or open a terminal and type sudo nautilus.

You should type "gksudo nautilus" for both.  If you just use sudo, you may mess up your ICEauthority.  Read about that in the Root/Sudo link in post #4.

---

