---
title: "applications menu gone."
date: 2008-05-03
forum: General Help
---

### Post by skeetwood-mac on 2008-05-03
I kept getting some gnome error when I would install packages so I thought maybe I'd try reinstalling some of the gnome packages. It seemed to go fine. then I installed a game through synaptic. Now my applications menu is gone. It still says applications but when you click on it theres no actual menu. And when I go to system>preferences>Main Menu I get an error window that says Application problem. Sorry, Main Menu closed unexpectedly.

---

### Post by chrisccoulson on 2008-05-03
First of all, make sure you've still got all the necessary packages installed:
```
sudo apt-get install ubuntu-desktop
```

Try logging out and back in again if ubuntu-desktop wasn't installed.

If ubuntu-desktop was already installed or installing it doesn't fix it, try creating a new user and see if they have the same problem.

If the problem is specific to your user profile, try:
```
rm -r ~/.config/menus
```

---

### Post by skeetwood-mac on 2008-05-03
I tried reinstalling ubuntu-desktop. Its still not working. I couldn't make a new user because the "add user" button was greyed out. But just for fun I tried that last code with still no luck.

---

### Post by chrisccoulson on 2008-05-04
The 'Add User' button is greyed out until you press the 'Unlock' button and authenticate

---

### Post by skeetwood-mac on 2008-05-04
alright well I made a new user and there's still no applications menu. So I think Im gunna try a different distro. Maybe one thats not so buggy.

---

### Post by chrisccoulson on 2008-05-04
No need to do that.

Now we know that this is a system-wide issue and not a user profile issue.

Could you post the files in /etc/xdg/menus (attach them as opposed to posting contents in-line)

---

### Post by skeetwood-mac on 2008-05-04
This is the contents of etc/xdg/menus

debian-menu.menu
gnomecc.menu
gnome-screensavers.menu
preferences.menu
settings.menu

---

### Post by chrisccoulson on 2008-05-04
I actually meant to post the contents of the files, but, nevermind - you're missing an applications.menu file anyway. Try reinstalling gnome-menus and see if that helps.

---

### Post by skeetwood-mac on 2008-05-04
ok I tried that with no luck. How could I have accidentally deleted the applications.menu file? Any other suugestions?

By the way. I really appreciate all this help. It would have taken me forever to figure this stuff out without all the help I've got on this forum from people like you.

---

### Post by chrisccoulson on 2008-05-04
Did reinstalling gnome-menus recreate the applications.menu file? If it hasn't, you could try downloading the gnome-menus deb package from [**_http://packages.ubuntu.com/_**]("http://packages.ubuntu.com/"), then doing this (in the directory that you downloaded the file to):
```
dpkg -x gnome-menus_2.22.1-0ubuntu1_i386.deb
sudo cp etc/xdg/menus/*.menu /etc/xdg/menus
```
Change the version of gnome-menus to the one you downloaded appropriate for your platform (the example I gave is Hardy 32-bit). This basically extracts the files from the package, and then copies the menu files to the appropriate location.

You'll probably need to log out and back in again

---

### Post by skeetwood-mac on 2008-05-04
ah finally! My applications menu is back! Thanks again for the help!

---

