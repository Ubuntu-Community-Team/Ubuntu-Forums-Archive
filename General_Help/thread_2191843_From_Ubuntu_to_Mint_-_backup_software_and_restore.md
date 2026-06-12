---
title: "From Ubuntu to Mint - backup software and restore"
date: 2013-12-04
forum: General Help
---

### Post by jack_walker on 2013-12-04
Hi,

I have ubuntu 13.04, I downloaded Linux Mint 16 and I want to  install it over my old ubuntu I'm using now. 
I would like to save the software list and restore it after a freshMint  13.10 installation, but I want to reinstall only some packages, 

  Example:
  I don't want to restore all unity packages. 
I don't want to restore all lib packages that are  installed at this moment, 
so I would like to restore only software that I  have downloaded and installed after the first ubuntu installation (so  only user software).

Is there a way to do that? What do people who want to change distro do when they want to backup their software, ppa and home configuration folders?

Thanks

---

### Post by oldfred on 2013-12-04
I am not sure you can get the list you want directly.

This lists all packages and is a text file so you can delete anything you want. But it includes all the lib so is very long.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

This lists top level apps but cannot directly be used to reinstall.
      
 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

   Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install

   Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'
sudo aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' >toplevelonly
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

   
A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'

Some other places to look.

 Main desktop apps:
 ls /usr/share/applications/
Apps that are installed
cd /var/lib/dpkg/info

---

### Post by sammiev on 2013-12-04
I test a lot of Linux OS and can usually add all the programs I want within 30 min of the install. Why carry anything over? Just use what they already have and add what you need. I wouldn't mix the two OS as there is difference between the two.

---

