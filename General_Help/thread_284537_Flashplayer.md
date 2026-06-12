---
title: "Flashplayer"
date: 2006-10-25
forum: General Help
---

### Post by dc12volthippy on 2006-10-25
Help! When I try to install Flshplayer I get this: ----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): y
cp: cannot stat `/tmp/fr-A6lyc3/install_flash_player_7_linux/libflashplayer.so': No such file or directory
cp: cannot stat `/tmp/fr-A6lyc3/install_flash_player_7_linux/flashplayer.xpt': No such file or directory
chmod: cannot access `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory
chmod: cannot access `/usr/lib/firefox/plugins/flashplayer.xpt': No such file or directory

Installation complete.
WTF?

---

### Post by madmetal on 2006-10-25
open a terminal and give 
sudo chmod 777 libflashplayer.so
to change the file permission and then 
sudo mv libflashplayer.so /usr/lib/firefox/plugins
to move it to the firefox plugins folder..

---

### Post by Treviño on 2006-10-25
Why still using flash 7?

Upgrade to 9 ;)

---

### Post by dc12volthippy on 2006-10-26
How do you get flash 9?

---

