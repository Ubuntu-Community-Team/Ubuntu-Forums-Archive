---
title: "Cannot get guest account to show up at login in Lubuntu"
date: 2015-09-20
forum: General Help
---

### Post by Adrian_Moncloa on 2015-09-20
I have a couple of extra accounts set up with User Groups in the GUI of Lubuntu but they do not show up when I reboot the machine.  Only the main administrator account that I set up with a password shows up.

Also, I would like to know how to install OpenOffice on Lubuntu.

Finally, I would like some guidance in how to limit what a guest can do in Lubuntu.  I would not like a guest to have access to any terminal applications for example.

Thanks in advance,

---

### Post by ajgreeny on 2015-09-21
> **Adrian_Moncloa said:**
> I have a couple of extra accounts set up with User Groups in the GUI of Lubuntu but they do not show up when I reboot the machine.  Only the main administrator account that I set up with a password shows up.

Also, I would like to know how to install OpenOffice on Lubuntu.

Finally, I would like some guidance in how to limit what a guest can do in Lubuntu.  I would not like a guest to have access to any terminal applications for example.

Thanks in advance,
I think we need a lot more detail about exactly how you added user accounts to your system in order to let you know what you might need to do; did you make /home folders for each of them; let's see the output of terminal command ```
ls /home
```
Do you have to have OpenOffice?  Libreoffice, which is now the default in most Linux distros and is a "better" OpenOffice, is in the repos so you can install that in the usual manner with software-center, synaptic or command ```
sudo apt-get install libreoffice
```
Limiting what a normal user can do in the way you are asking is not such a simple question to answer.  You, as first user, will have admin rights by using sudo and then using your user password; all other users added after that will not be able to use sudo so will not be able to do much that could affect the system or OS, only their own home.  Why do you want to stop them using terminal?  Without the ability to carry out any actions in the system area, they can cause no harm and terminal can be incredibly useful for some commands even within your own home so it is not necessary to remove that from other non-admin users.

---

### Post by Adrian_Moncloa on 2015-09-21
output of "ls /home" is
am guest mhcan

where am is my username and guest and mhcan are the two users I want to show up in the login screen

---

