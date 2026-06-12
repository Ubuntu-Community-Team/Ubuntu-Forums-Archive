---
title: "permission denied...."
date: 2007-06-03
forum: General Help
---

### Post by vj air on 2007-06-03
ok, im starting from scratch again on my veejay install atempt....

i first have to install ffmpeg and it says :

[B]Veejay requires a recent ffmpeg.

$ svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
$ cd ffmpeg
$ ./configure --enable-shared --enable-swscaler --enable-dts --enable-gpl
$ make
$ make install[/B]

it seems ok until i get to the last line   **$ make install**   at which point i get this :

[B]make -C vhook install
make[1]: Entering directory `/home/vj/ffmpeg/vhook'
install -d "/usr/local/lib/vhook"
install: cannot create directory `/usr/local/lib/vhook': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/vj/ffmpeg/vhook'
make: *** [install-vhook] Error 2[/B]

how do i enable permission for it to create the directory?

thanks.

Arran.

---

### Post by Nussbaum on 2007-06-03
Im pretty newb so just a guess but i wouldnt be suprised if you typed 'sudo make install' instead you execute the command as root and that way have the needed permission.

---

### Post by vj air on 2007-06-03
*passes a beer to Nussbaum*  :D

---

### Post by qx! on 2007-06-09
sudo make install 
instead of
make install
should help

---

