---
title: "Remove wrong files hidden in my computer"
date: 2014-03-17
forum: General Help
---

### Post by M1ck4el on 2014-03-17
Hi all,
I have a problem : 
I tried to install OpenOffice on Ubuntu
but my installation failed 
(at the extremly end cause LibreOffice was already installed)
I used # dpkg -i *.deb
---> installation of many files


So I have several useless files in my computer

Do you know how I can find and REMOVE them please?

---

### Post by deadflowr on 2014-03-17
What useless files do you have, the libreoffice files?
Simply remove or purge them.
When installing openoffice I always use purge
see man apt-get
for the difference between remove and purge.
```
sudo apt-get purge libreoffice*
```

---

### Post by Rakesh_vijayan on 2014-03-17
use the command sudo apt-get  autoremove autoclean

---

### Post by ajgreeny on 2014-03-17
Just remember that none of those commands or actions will remove any files or folders relating to Libreoffice, eg ~/.config/libreoffice, that are in your /home.

If you really must, you can delete them yourself, but is it really necessary?  You might want Libreoffice back at some point in the future, and those personal configuration folders and files will be very useful

---

