---
title: "Gnome icon-theme Buuf"
date: 2013-01-17
forum: General Help
---

### Post by Cavsfan on 2013-01-17
If any one is interested in having a nice icon theme, at least I think so. I installed this one on all the Ubuntus I have installed.
The instructions below will work with the latest versions of Ubuntu which have **Gsetttings**.
Very good specific instructions for installing these in **Lucid** are right [[COLOR=blue]_here_[/COLOR]]("http://www.liberiangeek.net/2010/07/manually-install-icon-themes-ubuntu-10-04-lucid-lynx/").
For Lucid you could still use the **wget** command below to obtain the file.

Here are the instructions: 
(You **may** get the already exists error on the 2nd line)

```
wget -O buuf3.6.tar.xz http://goo.gl/VJysV
mkdir ~/.icons
tar Jxf buuf3.6.tar.xz -C ~/.icons
```Then a quick way to put them to use is entering this in terminal:

** gsettings set org.gnome.desktop.interface icon-theme 'buuf3.6'**

This changes all of your icons but, I really noticed the ones in Cairo Dock.
The ones for Firefox and Thunderbird are pretty sweet!  :guitar:

[[IMG]http://ompldr.org/taDQ2cg[/IMG]]("http://ompldr.org/vaDQ2cg")

---

### Post by Cavsfan on 2013-04-26
> **Cavsfan said:**
> Then a quick way to put them to use is entering this in terminal:

** gsettings set org.gnome.desktop.interface icon-theme 'buuf3.6'**

This changes all of your icons but, I really noticed the ones in Cairo Dock.
The ones for Firefox and Thunderbird are pretty sweet!  :guitar:

The above **gsettings** command did not work in the new release of Raring Ringtale. 

What did work was installing gnome-tweak-tool **sudo apt-get install gnome-tweak-tool** if it is not already installed.

Install the icon theme into the .icon folder as above if you haven't already.

Then open tweak tool from (gnome fallback) Applications > System Tools > Preferences > Tweak Tool.
Click on Theme on the left and then Icon Theme on the right and then select Buuf3.2. It changes the icons instantly.

Not quite sure why but you get buuf3.2 when you download to above file. It's all good though.

---

### Post by Cavsfan on 2013-04-26
Even better yet get the Buuf 3.8 icon set from here [http://linux.softpedia.com/get/Desktop-Environment/Icons/Buuf-31950.shtml](http://linux.softpedia.com/get/Desktop-Environment/Icons/Buuf-31950.shtml)

Don't follow the instructions on that page, just download it.
Then enter in terminal **cd Downloads && tar Jxf buuf3.8.tar.xz -C ~/.icons**

If you are using Mint and the .icon directory does not exist just create it and it will work fine.

You don't need to logout and back in. Just enter **gsettings set org.gnome.desktop.interface icon-theme 'buuf3.8'** and It will take effect immediately.

---

### Post by Cavsfan on 2013-11-12
Version 3.10.0 of Gnome icon-theme Buuf is available.
[http://linux.softpedia.com/get/Desktop-Environment/Icons/Buuf-31950.shtml](http://linux.softpedia.com/get/Desktop-Environment/Icons/Buuf-31950.shtml)

---

### Post by Cavsfan on 2013-11-12
If ~/.icons does not exist create it **mkdir ~/.icons** then once downloaded enter **cd Downloads && tar Jxf buuf3.10.tar.xz -C ~/.icons**

Then enter **gsettings set org.gnome.desktop.interface icon-theme 'buuf3.10'** and it will take effect immediately.

---

