---
title: "Graphic problems at login"
date: 2007-06-30
forum: General Help
---

### Post by Malefic on 2007-06-30
A related problem I was having during installation is seen in this thread, as well as my system specs:
[http://ubuntuforums.org/showthread.php?p=2901631#post2901631](http://ubuntuforums.org/showthread.php?p=2901631#post2901631)
I did follow through on the solution to use the text-based installer.

Currently the userID // password screens are coming up like normal, but then the screen is heavily distorted with horizontal lines after the password is entered. The only solution at that point is a hard reset.

Any help is appreciated, Thanks.

---

### Post by confused57 on 2007-06-30
> **Malefic said:**
> A related problem I was having during installation is seen in this thread, as well as my system specs:
[http://ubuntuforums.org/showthread.php?p=2901631#post2901631](http://ubuntuforums.org/showthread.php?p=2901631#post2901631)
I did follow through on the solution to use the text-based installer.

Currently the userID // password screens are coming up like normal, but then the screen is heavily distorted with horizontal lines after the password is entered. The only solution at that point is a hard reset.

Any help is appreciated, Thanks.
When you get to the login screen, press "Ctrl+Alt+F1", this will get you to a console, login, enter:
```
sudo /etc/init.d/gdm stop
```
then edit your xorg.conf to use the "vesa" video driver:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo nano xorg.conf
```

page down to the video device section...change the driver to "vesa", with quotes.
Save the file by...Ctrl+X, y, enter.

then try restarting GDM:
```
sudo /etc/init.d/gdm start
```

If you're able to get to the GUI, then you can read over this link for installing "nvidia" drivers for your card:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

