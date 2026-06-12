---
title: "Chromebook: Update and change desktop"
date: 2014-06-21
forum: General Help
---

### Post by jsnwfta on 2014-06-21
I just got Ubuntu for my chromebook, i need help trying to update it and change the desktop. Can anyone help?

---

### Post by TheFu on 2014-06-22
There is nothing special about changing the desktop on an x86 chromebook vs any other laptop.
**sudo aptitude install {insert-new-DE-here}**
The logout, and on the login screen, click the "gear" to select a different DE.
I like LXDE, but others love XFCE4.  It is a chromebook, so the newer, fancy DEs don't really work all that great - too much GUI cheese. ;)

So ... which chromebook do you have? ARM or Intel?
What have you tried already?  Why didn't it work?
Oh ... and which release are you running?  I'm using 14.04, but the chromebook ran 13.10 nicely too.

---

### Post by jsnwfta on 2014-06-22
I have ARM
ver. 12.04
I tried to get Cinnamon desktop environment. i get this message "E: Unable to locate package cinnamon"
I used these 3 commands:
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install cinnamon


Also if i try this command: "[B]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable"
[/B]I get this in the terminal:"Cannot access PPA, to get PPA info, please check your internet connection.
and my internet is fine.

---

### Post by TheFu on 2014-07-16
I didn't check, but suspect there isn't an ARM architecture build for that package.  I have used LXDE on ARM - could that work for you?

---

