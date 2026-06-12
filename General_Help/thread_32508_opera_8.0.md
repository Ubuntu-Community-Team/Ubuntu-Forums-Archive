---
title: "opera 8.0"
date: 2005-05-08
forum: General Help
---

### Post by toto23 on 2005-05-08
does anybody know how to install opera 8.0 in Hoary 5.04.I got the installation packet  but i couldnt install it.

---

### Post by weblars on 2005-05-08
Installation is easy:

sudo dpkg -i nameofpackage.deb


I had problems with Opera crashing on my Ubuntu install when I used the standard packages provided for Ubuntu. The .6 packages (i.e. opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb) you can find on ftp.opera.com worked for me.

---

### Post by toto23 on 2005-05-08
[QUOTE=weblars]Installation is easy:

sudo dpkg -i nameofpackage.deb


I had problems with Opera crashing on my Ubuntu install when I used the standard packages provided for Ubuntu. The .6 packages (i.e. opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb) you can find on ftp.opera.com worked for me.[/QUOTE]
where should i put the package to access it.

---

### Post by ming0 on 2005-05-08
the package can go anywhere--i put them on my desktop so I can easily delete them after installing them.

Just make sure you download the Debian Static .deb :)

---

### Post by Xian on 2005-05-08
[QUOTE=ming0]Just make sure you download the Debian Static .deb :)[/QUOTE]
Why the static package?

---

### Post by ming0 on 2005-05-08
because opera requires QT, and because ubuntu doesn't install QT by default, the dynamically linked package won't work (if I remember correctly)

---

### Post by tread on 2005-05-08
Even if you get the shared version, just one library is required. (libqt3, you'll get the name when the install fails :))

---

