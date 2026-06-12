---
title: "how to install offline update repository in ubuntu 18.4"
date: 2019-09-29
forum: General Help
---

### Post by sagarwayal8888 on 2019-09-29
I am not able to install offline updates on ubuntu 18.4 please suggest to install it on offline :confused:

---

### Post by Skaperen on 2019-09-29
offline would be very difficult, time consuming, and use a lot of resources.  you would need to keep a replica of the repository, do do this without internet access to an online repository.

hopefully, someone knows a way to determine which packages you need to install or upgrade, so you can download to upgrade while offline.

could you tell us more about your offline needs in case someone can come up with a clever idea.

---

### Post by coffeecat on 2019-09-29
Support thread, not chat.

*Thread moved to **General Help**.*

---

### Post by Holger_Gehrke on 2019-09-29
There's a program called 'apt-offline'. Since it's written in Python you can even run it on Windows if you don't have access to a connected machine running Ubuntu, though you do not to install Python on Windows. Details [here]("https://docs.xubuntu.org/1804/user/C/offline-packages.html") and [here]("https://debian-administration.org/article/648/Offline_Package_Management_for_APT"). Some hints on using it on Windows [here]("https://superuser.com/questions/643528/apt-offline-on-windows").

Holger

---

