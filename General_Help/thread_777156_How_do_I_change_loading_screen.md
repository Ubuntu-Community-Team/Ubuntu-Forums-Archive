---
title: "How do I change loading screen?"
date: 2008-05-01
forum: General Help
---

### Post by Dead_$partan on 2008-05-01
Hi All,

Hope someone can help.  I am trying to change the graphical loading screen in ubuntu 8.04, I donwloaded the start up manager app and tried doing it this way.  I downloaded a .so file which was saved tot he home directory and using the startup manager I selected this new file but now I dont get any loading screen, just the test based screen.  I tried reverting to ortiginal settings but thsi didnt resolve.

Does anyone know what has gone wrtong here?  is there a manual way you gcan do this?  Some text configuration file or something I need to modify?

Thanks.

---

### Post by cdenley on 2008-05-01
If you're talking about the usplash screen, I've done something like this before
```

sudo apt-get install build-essential fakeroot dpkg-dev
apt-get source usplash-theme-ubuntu
sudo apt-get build-dep usplash-theme-ubuntu
cd usplash-theme-ubuntu-0.18

```
Replace or edit the images in the current working directory.
```

dpkg-buildpackage -rfakeroot -b
sudo dpkg -i ../usplash-theme-ubuntu_0.18_*.deb

```

I think there is a strict limit about how many colors you can use. I don't remember exactly.

The actual compiled theme is located at /usr/lib/usplash/usplash-theme-ubuntu.so. It has to be compiled for the correct platform (x86,AMD64). If you replace it, you have to run "sudo update-initramfs -u".

---

