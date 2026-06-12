---
title: "Trouble installing Macromedia Flash"
date: 2007-08-30
forum: General Help
---

### Post by DANGISE on 2007-08-30
Having trouble installing flash. After entering this command in terminal:sudo aptitude update && sudo aptitude install flashplugin-nonfree

it get this: No candidate version found for flashplugin-nonfree

The following packages have been kept back:

  libwrap0 

0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Writing extended state information... Done


What can I do?

---

### Post by ThrobbingBrain66 on 2007-08-30
Have you enabled your universe and multiverse repos?

System > Administration > Software Sources

Then tick the boxes for the Universe and Multiverse repos.  Close out the window and reload your sources like you mentioned above and issue the command you used above.

---

### Post by DANGISE on 2007-08-30
Universe and Multiverse repos were ticked, tried it again and same response.

---

### Post by ThrobbingBrain66 on 2007-08-30
That's very odd. Am I correct to assume you're running Feisty...maybe the 64-bit version?

If you're running 32-bit Feisty, just download the package here:
[http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb)

EDIT: Does the flash plugin show up in Synaptic?

---

### Post by DANGISE on 2007-08-30
yes, running feisty. tried to download the package and get :
ERROR WRONG ARCHITECTURE i386

---

### Post by rsambuca on 2007-08-30
There is no 64bit flash plugin as adobe has not made one, and has not open-sourced their software.  However, do not worry as there is an easy workaround, and a good fellow by the name of Kilz on these forums has created a script for you to run and install everything you need.

[[COLOR="Red"]The link is here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1174435&postcount=1")

---

