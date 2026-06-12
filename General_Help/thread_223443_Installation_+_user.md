---
title: "Installation + user"
date: 2006-07-26
forum: General Help
---

### Post by rob3000 on 2006-07-26
hello,

I have a question referring to the user which was created during the installation of ubuntu. In my case this is rob. I always log into the system with this username.

But why is rob in the adm and admin group? - I thought admin rights should only have the root-user?

regards

---

### Post by taurus on 2006-07-26
The reason rob belongs to adm & admin because rob sometimes needs to use sudo to run some root commands like editing systel files & updating system with apt-get/aptitude/synaptic.  But if you think rob shouldn't be able to do all that, then remove rob from groups adm & admin and rob can't do jack to system anymore...  That also means you can't do anything to system since there is no root password and you need to use sudo!!!  :rolleyes:

---

