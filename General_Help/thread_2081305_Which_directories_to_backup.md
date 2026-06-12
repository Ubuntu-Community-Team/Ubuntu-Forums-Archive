---
title: "Which directories to backup"
date: 2012-11-06
forum: General Help
---

### Post by PaperPilot on 2012-11-06
I have used Deja Dup to backup my home directory, and it has worked fine for restoring accidentally deleted files and when I installed a new hard drive.  Should I buy a new computer and install Ubuntu, which system directories should I backup in order restore the software additions I have made to this machine?

---

### Post by oldfred on 2012-11-06
/home has all your user configurations.

If installing the same version you can reinstall the software, otherwise you need to export the list of installed apps and reinstall as it will use newer versions. 

If you manually edited some system wide configuration files in /etc, you may want to back those up, but if a new version do not automatically copy back. Some may not be needed, some may conflict and some may be required or different.

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I use rsync but this is what I backup:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

