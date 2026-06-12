---
title: "Freezed login Ubuntu 14.04"
date: 2015-01-27
forum: General Help
---

### Post by Naelehed_Suirad on 2015-01-27
My problem started after i rebooted my pc ,after booting everything went  ok untill the login screen where i type my password an then it freezes  ,nothing happens , i can't get to tty shell by alt+ctrl+f1..f6 , i have a  fluxbox windows manager i can list my files from there but i can't  acces my original enviroment , My filesystem is "full" and won't boot  right.  I am booted into an ubuntu USB.  How can I clear out space and  restore my working filesystem? , i belive this is the problem .. what  can i do to acces my system? I really want to recover my files ,tabs opened at that moment

---

### Post by kc1di on 2015-01-27
There are a couple things you can do.
From the Live Usb you should be able to access your files and delete some that are no longer needed. 
then you can install gparted if it's not already there and resize the partition in question to give it more room , back up important files first.
if you can't do it with the live disc. then down load a copy of puppy linux and it will allow you to mount and back up important files then 
do a complete re install and make sure you give yourself enough space on the H.D. 
Good Luck

---

### Post by Naelehed_Suirad on 2015-01-27
the drive is already mounted. before i rebooted my pc i saw some warning regarding low disk space on the home directory .. i can acces all my drive but my home folder i can't . it is encrypted and the drive appears to be already mounted...

---

### Post by kc1di on 2015-01-27
[This artical]("http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/") may be of help to you.

---

### Post by Naelehed_Suirad on 2015-01-27
Thanks sir . It really helped me . One more question, you think i should backup and reinstall the system or just make some space by deleting files that are no longer needed , and if i try to delete them even from gksu nautilus i don't have permission to delete them only to copy them ..

---

### Post by Naelehed_Suirad on 2015-01-27
Can't change permission to delete  files : read only file system , how could i make some space so my pc could boot properly again ?

---

