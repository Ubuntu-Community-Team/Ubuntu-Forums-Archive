---
title: "Restricting a GUI user to perform only predefined actions on Ubuntu"
date: 2021-10-21
forum: General Help
---

### Post by bleepx on 2021-10-21
Hello,


I am the admin of an Ubuntu machine, which I want to let a user "guest" login to via GUI.  This user should be able to perform only certain actions (like view the contents of some files located on the desktop etc), and Shutdown / Reboot. Nothing else, like using the browser, email, edit their own files etc. How can this be done?


Thanks

---

### Post by vanadium on 2021-10-21
```
man polkit
``` if you want to do it thoroughly. Otherwise, there are some tricks to keep "the honest user out" by for example setting the executable PATH to a single dedicated folder that only contains the executables you want the guest to run, hide all launchers you don't want the guest to see, restricting file permissions in the home folder of the user, not give access to a graphical terminal (there still remaind an Alt+F2 run dialog though...).

---

### Post by ActionParsnip on 2021-10-21
Are you making a faux Citrix server? If not and you want users want to manage files, they can do this over the network using the local file manager rather that accessing a full desktop session on the remote system. Linux and Mac file manager can connect to SFTP (Given when you install openssh-server) and remote files will be manageable. This will be managed by the Ubuntu file permissions as you expect

---

### Post by dragonfly41 on 2021-10-21
Possibly webmin can do this for you .. through localhost:10000 https connection.
It is easy to set permissions per user. All accessed through browser including files manager.

[https://www.webmin.com/](https://www.webmin.com/)

---

### Post by dragonfly41 on 2021-10-21
sorry .. duplicate post

---

