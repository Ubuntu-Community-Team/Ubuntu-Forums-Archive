---
title: "[SOLVED] Please Help Me With Fixing OpenOffice!!"
date: 2008-02-02
forum: General Help
---

### Post by alsamman on 2008-02-02
to make a long story short, i screwed up oo and now im getting this annoying error when i try to install or remove openoffice files:
```

E: openoffice.org-hyphenation: subprocess post-installation script returned error exit status 127
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured

```

I am dieing for assistance I want to get this done and over with. Im trying to install the debs from the oo site but i cant because it says i have dependancy problems

---

### Post by seventyeights on 2008-02-02
Why don't you reinstall it with synaptic?

---

### Post by alsamman on 2008-02-02
right now openoffice isnt installed on my computer but when i try to, in the process i get those errors and right now im just asking for these errors to get resolved

---

### Post by alsamman on 2008-02-03
bumppppppp

---

### Post by alsamman on 2008-02-03
bump

---

### Post by forestpixie on 2008-02-03
when I've removed the ubu version and installed the oo version I remove all the openoffice that synaptic finds

then I followed this 
[http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

---

### Post by alsamman on 2008-02-03
> **forestpixie said:**
> when I've removed the ubu version and installed the oo version I remove all the openoffice that synaptic finds

then I followed this 
[http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

i know how to install oo from the website, that isnt the problem. The problem is that when i try to install openoffice or uninstall it, i get the same errors if i were to try in synaptic or the file from the oo website. So i am asking how can i get rid of these errors i get when i install/uninstall oo. Installing oo from the website is a different issue, i can deal with that, but in order to make these installations work i must get rid of the errors

---

### Post by drs305 on 2008-02-03
Have you tried:
```
sudo apt-get remove --purge openoffice.org
```

---

