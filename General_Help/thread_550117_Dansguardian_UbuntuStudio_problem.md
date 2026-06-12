---
title: "Dansguardian UbuntuStudio problem"
date: 2007-09-13
forum: General Help
---

### Post by loftcs on 2007-09-13
I recently tried to install Dansguardian on a pc with UbuntuStudio by following this tutorial:
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

during the download and install there were errors that referred to clamav but since the tutorial mentions getting clamav errors I didn't pay much attention

when I try to edit the dansgaurdian.conf file:
 sudo gedit /etc/dansguardian/dansguardian.conf

I get an empty file in the text editor i.e. there is no text.......I then went to the directory and found that all files had the following extension

.dpkg-new (e.g. dansguardian.conf.dpkg-new)

when I tried to open the the .dpkg-new file I got an access denied message

being an absolute novice in ubuntu I even tried opening the file directly and saving a copy with out the .dpkg-new extension but when I tried to do the following:
sudo dpkg-reconfigure dansguardian

I get an error that says dansguardian is broken or not installed properly

any help would be greatly appreciated

---

