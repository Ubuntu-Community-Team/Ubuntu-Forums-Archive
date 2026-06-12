---
title: "installed programs"
date: 2014-11-22
forum: General Help
---

### Post by kccv42 on 2014-11-22
How do i view on installed programs in a user friendly way similiar to how windows 7 shows them in their "add and remove" application?

---

### Post by yancek on 2014-11-22
How about the Software Center.

---

### Post by oldfred on 2014-11-23
I like synaptic, but they do not install it by default anymore.

sudo apt-get install synaptic

You can select to see it sorted many ways including installed or even how installed. It will not show applications you may have totally installed outside of dpkg, Software Center or synaptic.

---

### Post by kccv42 on 2014-11-24
I tried synaptic but it is hard to see all the packages installed.

---

### Post by oldfred on 2014-11-24
If you click on installed it shows just the installed apps.

You can also create lists of installed apps. But this list includes all the lower level support files and becomes a very long list.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages

If just wanting info, not a list to reinstall:
      
 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

---

