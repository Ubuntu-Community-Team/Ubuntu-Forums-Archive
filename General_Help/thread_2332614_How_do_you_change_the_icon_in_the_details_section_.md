---
title: "How do you change the icon in the details section of settings?"
date: 2016-08-02
forum: General Help
---

### Post by mcBOSS on 2016-08-02
I was wondering if you are able to change the icon in this section of the settings, thanks.

---

### Post by nikefalcon on 2016-08-02
> **mcBOSS said:**
> I was wondering if you are able to change the icon in this section of the settings, thanks.

Is this the logo you are referring to?
[ATTACH=CONFIG]270542[/ATTACH]

---

### Post by mcBOSS on 2016-08-03
Yes, that's the one.

---

### Post by nikefalcon on 2016-08-04
Apparently, you will have to get the source to make changes. In a new directory do:
```
 apt-get source gnome-control-center gnome-control-center-data 
```
Then replace the logo.
```

cd gnome-control-center-3.18.2/
cp /home/user/wherever/UbuntuLogoBlank.png debian/UbuntuLogoBlank.png 

```
Now configure, make and install the package. Watch out for errors while configuring; most likely you will have to install a lot of development files. (libgtk3-dev and such)

Use this article as a guide: [https://community.linuxmint.com/tutorial/view/162](https://community.linuxmint.com/tutorial/view/162)
Note that you can skip step 1, and install only packages you need by looking at the output of **./configure**. (Although you will need **intltool**,** libgtk3-dev **and many more before you can configure successfuly.)

Good Luck!

EDIT: Reference: [https://askubuntu.com/questions/623613/wrong-distro-and-logo-in-gnome-control-center](https://askubuntu.com/questions/623613/wrong-distro-and-logo-in-gnome-control-center)

---

