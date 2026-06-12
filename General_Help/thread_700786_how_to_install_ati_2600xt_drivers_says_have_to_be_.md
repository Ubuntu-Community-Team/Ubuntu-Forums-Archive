---
title: "how to install ati 2600xt drivers says have to be a super user please help."
date: 2008-02-18
forum: General Help
---

### Post by darkwooly on 2008-02-18
i just installed ubuntu for the first time and i wondering how to install the ati 2600xt drivers. It wont let me because it says  says have to be a super user. I dont know how to do this.
these drivers i got from the ati  website and chose the linux drivers .
thanks

---

### Post by arkara on 2008-02-18
ubuntu has installed the open source drivers for your ati card already.
the problem is that they do not support 3d graphics.
if you want to install the proprietary drivers  then don't do it the terminal way.just go to
system-->admin-->restricted driver manager and install it from there.
it will ask you a password. this pass is for the super user password. put yours there and then the drivers will install themselves automaticaly

---

### Post by Yellow Pasque on 2008-02-18
Follow this guide. If it asks for super-user permissions, use the sudo qualifier before a command, For example:
```
sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
```
Follow method 2 of this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Ubumble on 2008-02-18
Could you please post with the results after you try it?  I have had major problems using the new drivers with my HD 2600XT card and I'd like to see if anyone else is successful.  Thanks!

---

### Post by arkara on 2008-02-19
what problems do you have???
what is your card model?

---

### Post by Ubumble on 2008-02-20
It's a Sapphire 100218L  Radeon HD 2600XT (512 MB DDR3, PCIe x16).  I'm using 64-bit Ubuntu.

With both 8.01 and 8.02 drivers I have used "method 2" from the wiki.  Everything seems to work ok.  I reset the system and it boots up fine until X starts up.  At that point the machine locks up hard.  I have to reboot into single user mode and manually reset the the Xorg.conf file.  I've cleaned everything out and repeated this several times with the exact same results.  It also happens if I just reset X instead of rebooting after doing the driver install.  I've seen some people talk about similar results with AGP model 2600XT's, but I haven't seen any other reports about PCIe models.

Note, I haven't seen any graphics problems with Vista on this machine when using 8.1.

---

### Post by Yellow Pasque on 2008-02-20
Catalyst does not work with AGP cards. Follow the link in my signature to install the open-source radeonhd driver.

---

### Post by Ubumble on 2008-02-22
I'm using PCIe not AGP.

---

### Post by trr135 on 2008-03-03
Have you heard anything on this issue. I am having pretty much the same problem. Any help you could provide would be greatly appreciated.

---

### Post by Ubumble on 2008-03-05
Unfortunately not.  I've had similar problems under Fedora and Ubuntu.  I'm keeping my fingers crossed for the 8.03 release later this month.  :confused:

Actually 8.03 came out today so I'm off to try it.

---

