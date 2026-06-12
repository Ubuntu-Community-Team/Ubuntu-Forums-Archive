---
title: "Do I have to re-install everything after up-gradation?"
date: 2013-01-24
forum: General Help
---

### Post by Pensu on 2013-01-24
Hi, 

I am using Ubuntu 12.04 LTS. I want to upgrade to 12.10. But I have a lot of apps installed. I want to know, if I upgrade, will I have to re-install everything again? Or Ubuntu will take care of it?

---

### Post by RJLacroix on 2013-01-24
It depends on the choice you make when installing the 12.10 version. Once it starts from the CD and you choose "Install Ubuntu" from the icon on the upper left of the screen, the installation will begin and then you will see a prompt that gives you 3 installation choices, "Install Alongside 12.04LTS", which will try to keep all your apps and data, "Replace 12.04LTS with 12.10", which reformats the HD and allows 12.10 to take over all of the disc space, and finally, "Do Something Else" which allows you to make your own partition choices and is intended for advanced users.

---

### Post by jim_deadlock on 2013-01-24
If you're doing an upgrade via the Update Manager then you will still have all the same apps after the upgrade. The only exceptions are apps which are not compatible with your new version (which is quite rare).

---

### Post by oldfred on 2013-01-24
I would still make a list just in case.
I run the dpkg to create a new list with every rsync backup since I plan a new install and restore /home and all apps as worst case recovery.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by jim_deadlock on 2013-01-24
I like that oldfred, thanks. Will that also remove all the unwanted apps from a new install?

Edit: OK I see the answer to that is no.

---

### Post by oldfred on 2013-01-24
It is just a text list of apps without versions. You can manually edit but it is huge as it also has all the lower level apps. 

If you know what you want to remove best to do that first. If from an old install you do not want Open Office as the new default is LO and you do not want old kernels, maybe a few other things. 

But if you have a lot of apps it is difficult to remember what you want to reinstall.

---

