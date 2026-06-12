---
title: "Kubuntu splash Screen but use Ubuntu"
date: 2007-02-17
forum: General Help
---

### Post by Rhaddad on 2007-02-17
Hello, 
I recently installed the kubuntu desktop, and then removed it, but when i boot up my computer the Kubuntu progress bar comes up not the ubuntu one.

---

### Post by groggyboy on 2007-02-17
try this.  in the terminal:
```
sudo update-alternatives --config usplash-artwork.so
```
select the appropriate usplash (probably the first one).  then input the following into the terminal:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
reboot and enjoy!

to ensure that the Kubuntu progress bar is removed from your system, type this in terminal:
```
sudo aptitude remove kubuntu-artwork-usplash
```
it should have been removed when you uninstalled kubuntu, but it's possible it got left behind.

(taken in part from [the usplash customization wiki page]("https://help.ubuntu.com/community/USplashCustomizationHowto"))

cheers!

---

### Post by ciscosurfer on 2007-02-17
> **Rhaddad said:**
> Hello, 
I recently installed the kubuntu desktop, and then removed it, but when i boot up my computer the Kubuntu progress bar comes up not the ubuntu one.There are two things you can try.  First open a Terminal session and enter in the following:```
sudo update-alternatives --config usplash-artwork.so
```This will bring up a list of choices and you can (re)choose to use the original ubuntu usplash that came with your install (instead of the Kubuntu one that got added with you installed kubuntu-desktop).  After you pick the original usplash and exit out, you must now issue the following to get it to stick:```
sudo dpkg-reconfigure linux-image-`uname -r`
```(those are backticks, on the same key as the tilda -- you can also issue the uname -r part this way:```
sudo dpkg-reconfigure linux-image-$(uname -r)
```The second option to try, failing the first solution, is to manually reinstall the ubuntu-artwork package, so that the original ubuntu usplash get placed back in.  

A third solution (that I know I've used in the past when things get finicky) is to actually reinstall both the kubuntu-artwork-upslash and ubuntu-artwork packages, go through the steps I outlined in the first option to fix above (the command line stuff), and then manually removing kubuntu-artwork-usplash and/or kubuntu-desktop again.  Note that you DO NOT need to reinstall the entire kubuntu-desktop package, simply the kubuntu-artwork package.

Good Luck!

EDIT: groggyboy, you beat me to it!

---

### Post by Rhaddad on 2007-02-17
Hello,
Thanks brothers it works

---

