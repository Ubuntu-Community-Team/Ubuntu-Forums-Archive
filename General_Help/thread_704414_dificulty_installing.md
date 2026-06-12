---
title: "dificulty installing"
date: 2008-02-22
forum: General Help
---

### Post by AJS302 on 2008-02-22
recently i installed ubuntu 7.10 on an old computer of mine, i had to use ndiswrapper to get my wireless usb adapter working, once i'd installed everything the usb adapter worked fine and i had access to internet, but when i wanted to install amsn but it came up with an error saying that it couldn't find the package, i tried installing a few other things and all of them did the same, can any one help me?

---

### Post by taurus on 2008-02-22
I am sure that all your repos in /etc/apt/sources.list are disable because it couldn't find a network connection when you installed it.  Therefore, you need to enable them before you can install anything else.  Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close the gedit editing window.  

Then run

```
sudo apt-get update
```
See if you can install anything now.

---

### Post by PeterJS on 2008-02-22
I assume from your statement that you used the ndiswrapper you didn't have the network setup when you did the initial install. Gutsy does some rather dumb things when it can't find the internet when it's installed, like assume the internet must not exist. If you go to System > Administration > Software Sources, you should be good to g if you enable the 4 repositories on the front tab and try again.

---

