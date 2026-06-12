---
title: "tor browser untinstalled playonlinux/wine and had install problems."
date: 2014-01-16
forum: General Help
---

### Post by silvervulpus on 2014-01-16
so i was trying to install tor browser following the instructions on  this page.  [http://www.unixmen.com/protect-your-online-privacy-with-tor-browser/](http://www.unixmen.com/protect-your-online-privacy-with-tor-browser/). it  removed playonlinux/wine which i need for using painttoolsai. also it  gave me an error code upon installation like this.


Unpacking tor-browser:i386 (from .../tor-browser_2.3.25-12_i386.deb) ...
Unpacking tor-browser:i386 (from .../tor-browser_2.3.25-12_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tor-browser_2.3.25-12_i386.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor 0.2.4.20-1~precise+1
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor-browser_2.3.25-12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


ok WTF. so i stopped there.... i still want tor browser and isnt there  some way i can have tor browser and play on linux so i can keep doing  artwork. also. i dont think tor installed correctly because i have  received none of the pictures displayed on the instruction link i  posted, and this happens...


nita@ubuntu:~$ sudo chown -R nita ~/.tor-browser
chown: cannot access `/home/nita/.tor-browser': No such file or directory

---

### Post by silvervulpus on 2014-01-16
ok im a total moron... i was trying to install 32bit on my 64  system....... next question how do i undo all the dumbassery i just  committed so i can properly install the 64 bit... whats the command i  need to entirely remove what i accidentally installed by following the  32bit instructions instead of the 64 instructions... i know its going to be "sudo apt-get --purge" but i dont know what to type after i type the purge part? i feel so damned stupid right now >.<

---

### Post by Frogs Hair on 2014-01-16
Try the following.  

```
sudo apt-get remove --purge tor-browser
```

---

### Post by silvervulpus on 2014-01-16
yea... im retarded thanks a bunch dude. you actually helped me alot

---

### Post by silvervulpus on 2014-01-16
one more thing..... got it uninstalled and reinstalled properly yet again following the 64bit instructions on [http://www.unixmen.com/protect-your-...h-tor-browser/]("http://www.unixmen.com/protect-your-online-privacy-with-tor-browser/"). now the only problem i have left is
nita@ubuntu:~$ sudo chown -R nita ~/.tor-browser
chown: cannot access `/home/nita/.tor-browser': No such file or directory

---

### Post by silvervulpus on 2014-01-16
also, seems kinda stupid, but does anyone know if tails22 will run peerguardian without bug or if using peerguardian on tails22 will cause issues?

---

### Post by silvervulpus on 2014-01-16
Im still having problems with tor-browser because of the chowm. it never created the tor-browser directory in ~/home and now i have this error!

---

### Post by silvervulpus on 2014-01-16
still need help here.... bumpity bump bump bump

---

### Post by Frogs Hair on 2014-01-16
Please wait 24 hours to bump . I have used the Tor Browser Bundle just for trial purposes , but haven't not installed with method you are using. The bundle runs from a folder placed any where you want.

---

