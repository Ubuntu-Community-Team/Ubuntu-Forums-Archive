---
title: "need to get a list of installed programs..."
date: 2007-07-31
forum: General Help
---

### Post by Mia_tech on 2007-07-31
I've been running my vesion of ubuntu for quite some time and is time to clean the HD a bit, is there a way to get a list of all the programs installed on your computer?
also how could I display the folders with the most HD use?

thanks in advance.

---

### Post by az on 2007-07-31
dpkg --get-selections

will list all your installed packages

sudo dpkg -l
will also list all your packages.

But if you use the former, you are able to save it to a file and use that file to reinstall the packages on another system


sudo dpkg --get-selections > file

save the file to a usb disk.  Reinstall and then run

sudo dpkg --set-selections < file

and then

sudo apt-get dselect-upgrade

will install everyithing.

As for the most used folders, you probably only need to save stuff from your home drive.  Unless you need to back up a database or something.

---

### Post by Mia_tech on 2007-07-31
thanks

---

