---
title: "How to launch Kompozer"
date: 2015-06-07
forum: General Help
---

### Post by ufarmer on 2015-06-07
I followed the instructions to install Kompozer found at [http://askubuntu.com/questions/376986/kompozer-installation-step-by-step]("http://askubuntu.com/questions/376986/kompozer-installation-step-by-step").

These instructions link to another page that claims Kompozer is "now in the menu" after the installation.  However, I can't find it anywhere and the obvious command line argument "kompozer&" doesn't have any effect.

Does anyone know where to find it or how to launch it?

---

### Post by Bucky Ball on 2015-06-07
Where did you download Kompozer from? I installed it awhile ago and it is right there in the menu under 'Internet'. Didn't need to tweak. :-k

* I think I installed it from the official repositories, by the looks of it. Can't find a PPA for it (I try to avoid). I have never had to go through the rigmarole outlined on that link to install Kompozer . You could try [this]("http://sourceforge.net/projects/kompozer/"), extract and install if you can't find Kompzer in Software Centre.

PS: 'komposer&' is not going to work. It is not spelt like that. All you need in a terminal is 'kompozer', no ampersand&. Try that before anything else and see if you've actually successfully installed it.

---

### Post by ufarmer on 2015-06-07
Thanks.  "komposer" was a typo.  I meant "kompozer".  I just untarred the tar file but it is not in the "Internet" menu and fails to launch from the command line.  It is not clear if more steps are required for installation.  From the untarred "kompozer" directory, the following commands fail with the following complaints:

>> ./kompozer
(kompozer-bin:7035): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"

>> ./kompozer-bin
./kompozer-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

And the usage for this command is a little too terse for me:

>> ./nsinstall 
usage: ./nsinstall [-C cwd] [-L linkprefix] [-m mode] [-o owner] [-g group] [-DdltR] file [file ...] directory

---

### Post by ufarmer on 2015-06-08
The instructions here [http://linuxg.net/how-to-install-kompozer-1-0-8-beta-3-on-ubuntu-14-04-and-derivative-systems/]("http://linuxg.net/how-to-install-kompozer-1-0-8-beta-3-on-ubuntu-14-04-and-derivative-systems/") worked perfectly on 14.04.  After running:

> $ sudo sh -c 'echo "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe" >> /etc/apt/sources.list'
$ sudo apt-get update
$ sudo apt-get install kompozer
$ sudo sed -i '/precise/d' /etc/apt/sources.list

Kompozer is in Applications-->Internet and the command "kompozer" is sensibly in /usr/bin.

---

### Post by Bucky Ball on 2015-06-08
Excellent work and thanks for sharing the fix. Enjoy. :)

Please see the second link in my signature.

---

