---
title: "Ubuntu is freezing on login screen"
date: 2014-05-14
forum: General Help
---

### Post by wilson888888888 on 2014-05-14
I have ubuntu 14.04, and it was running normally until it crashed for no reason. Now whenever I try to boot it, it freezes on the login screen. I thought it might be because of the ram but memtest passes without any errors. I also tried doing quiet splash nomodeset in the grub but that doesn't work either.
How do I fix?

---

### Post by wilson888888888 on 2014-05-17
I've tried using dpkg to try to fix the packages, but it didn't help. Also tried reinstalling unity and lightdm, but that doesn't work either. An interesting thing I've noticed is that when I press the power button while it's booting, the login screen loads fine with the mouse and keyboard working. However it shuts off a few seconds later.

---

### Post by sammiev on 2014-05-17
You can try to press "Ctrl + Alt + F1" at the login screen. Terminal window will open. Press enter and it will ask you for your user name then password. After you login that way try to update and see if it reports any errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by wilson888888888 on 2014-05-17
It updated without errors, but the freezing at login screen persists. However, when I run sudo service lightdm restart, the login screen starts working, but when I try to login it freezes again.

---

### Post by sammiev on 2014-05-17
Well you know your OS is updated and there is no broken packages so the problem must lie with the login. Hopefully someone who had this problem steps in.

Have tried stopping and starting lightdm?

```
sudo stop lightdm
sudo start lightdm
```

---

### Post by wilson888888888 on 2014-05-17
When I stop and start lightdm the login screen seems to work, but when I try to login it freezes.

---

### Post by sammiev on 2014-05-17
You can try GDM instead if you wish.

You can try to press "Ctrl + Alt + F1" at the login screen. Terminal window will open. Press enter and it will ask you for your user name then password.

```
sudo apt-get install gdm
```

```
sudo dpkg-reconfigure gdm
```

```
sudo service lightdm stop
```

```
sudo service gdm start
```

Then you can try to login with user name and password.

---

### Post by wilson888888888 on 2014-05-18
gdm just causes it to hang on a black screen. I've given up and just reinstalled ubuntu.

---

