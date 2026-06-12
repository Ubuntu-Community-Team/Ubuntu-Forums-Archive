---
title: "Ubuntu suddenly zoomed in"
date: 2014-07-06
forum: General Help
---

### Post by haggag87 on 2014-07-06
Hi,

This is my first day of using Ubuntu. I was doing the steps to install nvidia and then suddenly I found the screen zoomed in and I don't know how to make it normal again.
This is how it looks like [ATTACH=CONFIG]254514[/ATTACH]
So if anyone could please assist me as this is very annoying to me and I want to continue my nvidia setup process.

---

### Post by robbie 348 on 2014-07-06
Have you tried resetting your resolution in "display"?

---

### Post by grumblebum2 on 2014-07-06
> **haggag87 said:**
> Hi,

This is my first day of using Ubuntu. I was doing the steps to install nvidia and then suddenly I found the screen zoomed in and I don't know how to make it normal again.
This is how it looks like [ATTACH=CONFIG]254514[/ATTACH]
So if anyone could please assist me as this is very annoying to me and I want to continue my nvidia setup process.
What steps were these exactly?

---

### Post by haggag87 on 2014-07-06
> **robbie 348 said:**
> Have you tried resetting your resolution in "display"?
I can't access it as the screen is zoomed and I can't see the rest of the settings.

---

### Post by haggag87 on 2014-07-06
> **grumblebum2 said:**
> What steps were these exactly?
the steps found here [http://pointclouds.org/documentation/tutorials/gpu_install.php](http://pointclouds.org/documentation/tutorials/gpu_install.php)

---

### Post by grumblebum2 on 2014-07-06
> **haggag87 said:**
> I can't access it as the screen is zoomed and I can't see the rest of the settings.
Use alt+right mouse to move window.

---

### Post by haggag87 on 2014-07-06
> **grumblebum2 said:**
> Use alt+right mouse to move window.
I did that but still only half the window is appearing

---

### Post by grahammechanical on 2014-07-06
Do you want my guess? You have gone into System Settings>Appearance>Behaviour and enabled workspaces. The workspace switcher icon is in the launcher and it is not there by default. We have to enable workspaces to get that icon. After that in the Appearance>Look tab you have maximized the launcher icon size.

By the way, if when we install we tick "install third party software" we get a proprietary video driver installed. So, why do you need to install a Nvidia driver? Also, we can install proprietary video drivers through System Settings>Software and Updates>Additional Drivers tab. A third point, with the installation of a proprietary video driver we get a settings manager for that proprietary video driver. Did you change the default settings in the Nvidia settings manager and has that action produced this effect?

Anyway, once we are running a proprietary video driver then System Settings>Displays is not used.

Regards.

---

### Post by haggag87 on 2014-07-06
> **grahammechanical said:**
> Do you want my guess? You have gone into System Settings>Appearance>Behaviour and enabled workspaces. The workspace switcher icon is in the launcher and it is not there by default. We have to enable workspaces to get that icon. After that in the Appearance>Look tab you have maximized the launcher icon size.

By the way, if when we install we tick "install third party software" we get a proprietary video driver installed. So, why do you need to install a Nvidia driver? Also, we can install proprietary video drivers through System Settings>Software and Updates>Additional Drivers tab. A third point, with the installation of a proprietary video driver we get a settings manager for that proprietary video driver. Did you change the default settings in the Nvidia settings manager and has that action produced this effect?

Anyway, once we are running a proprietary video driver then System Settings>Displays is not used.

Regards.
But how can I just get the normal screen resolution now? I can't even see this "Software and Updates" under settings

---

### Post by grumblebum2 on 2014-07-06
> **haggag87 said:**
> the steps found here [http://pointclouds.org/documentation/tutorials/gpu_install.php](http://pointclouds.org/documentation/tutorials/gpu_install.php)
I have no idea what PCL is and I'm not familiar with that method of installing a nvidia driver so I'll pass. Do you want to use PCL?
Did you check your nvidia card compatibility?
One thing I did notice, it tells you to **sudo service gdm stop** where in ubuntu it should be **sudo service lightdm stop**.

---

