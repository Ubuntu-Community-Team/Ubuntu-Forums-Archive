---
title: "Combing distributions"
date: 2018-12-14
forum: General Help
---

### Post by datzmrpig1862 on 2018-12-14
I have vanilla Ubuntu 18.04 installed on my laptop...but i also have a copy of 18.04 on usb that has specific software for building android roms and was wondering if there is a fast way to add all the apps from the specialized distribution to the Ubuntu on my pc without having to just reinstall or install app by app.

---

### Post by 1clue on 2018-12-14
Without knowing the list of software you're interested in nobody can help. And if you have a list of software -- and all of it is in the repository -- then you should be able to install it from your list directly.

---

### Post by oldfred on 2018-12-14
You can export a list of installed apps and reimport that.
But settings are in /home usually in hidden .folders.

You can also edit list at will as long as you keep format which is just text.
       If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

### Post by Dennis N on 2018-12-14
If an application was not installed with a Ubuntu package manager (or even if it was), you can just copy the executables and related program files to another OS but will have to manually create any menu entries or launchers that existed. Sometimes you may have to install some dependencies onto the 2nd OS as well. No guarantee it will work in every situation, but if both 18.04, I think it is likely to work.

I have done this quite a few times with game programs that provide no installer.

---

### Post by datzmrpig1862 on 2018-12-14
I just ended up backing up all my documents and installed the specialise distro cause it was the simplest way around it and just kinda took less time ...there was only a couple programs from the vanilla distro that wasnt on this one and i can get them in the package manager easy

---

