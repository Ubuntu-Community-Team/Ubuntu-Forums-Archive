---
title: "Wine and steam"
date: 2007-06-12
forum: General Help
---

### Post by andymushu on 2007-06-12
I know it has already been established that steam and wine version 0.9.38 don't work well together, so i installed  wine 0.9.37.tar.bz2 from sourceforge. after a lot of searching on google, i managed to figure out how to decompress the file. then i did the ./configure, make depend, and make. after that i did make install, which i assumed meant it installed wine. then i tried to run steam, but it says wine is not installed. any help would be much appreciated.

---

### Post by bashologist on 2007-06-12
Maybe try installing wine again with the last command being "sudo make install". That's my guess. Did you check if wine installed correctly before installing steam? Does the "wine" command work?

---

### Post by andymushu on 2007-06-12
i did sudo make install. it installed fine with no errors shown in the terminal. i installed steam after i installed wine version 0.9.38. i just uninstalled wine. i left steam on my system.

"The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine"

this is the error i get when i try to do "wine steam". obviously i don't want to install it from the repositories because they have only the newest version.

---

### Post by andymushu on 2007-06-12
bump

---

### Post by andymushu on 2007-06-12
bump

---

### Post by Gruelius on 2007-06-14
Just grab the .37 deb file from somewhere like i did, easy as to install.

---

