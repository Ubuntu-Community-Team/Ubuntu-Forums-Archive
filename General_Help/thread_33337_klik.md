---
title: "klik"
date: 2005-05-10
forum: General Help
---

### Post by JaceMan on 2005-05-10
Just curious if anyone knows if [klik](http://klik.atekon.de/) is compatible with Ubuntu.  I know that Ubuntu is Debian based, but Klik does not list it in its list of compatible distros.  I thought before I wasted my time, and possibly my OS - I'd take it to the community to find out for sure.

Come to think of it, I wonder if Klik only woks on x86 derivatives of Debian.  Hmm... the wheels are turning now.

---

### Post by JaceMan on 2005-05-10
Nevermind, I found [THIS](http://www.knoppix.net/forum/viewtopic.php?p=73016) thread in the Knoppix forums that was quite enlightening.  In fact, if any more of you are interested in [klik](http://klik.atekon.de/) you may [WANT TO CHECK THIS OUT](http://www.knoppix.net/forum/viewtopic.php?p=73016).

---

### Post by Dex on 2005-05-18
[QUOTE=JaceMan]Nevermind, I found [THIS](http://www.knoppix.net/forum/viewtopic.php?p=73016) thread in the Knoppix forums that was quite enlightening.  In fact, if any more of you are interested in [klik](http://klik.atekon.de/) you may [WANT TO CHECK THIS OUT](http://www.knoppix.net/forum/viewtopic.php?p=73016).[/QUOTE]
Hey Jaceman
I went hunting for klik for ubuntu and found your post. Your link to Probono has this script:
wget klik.atekon.de/client/install -O -|sh
wget *****/dialog_1.0-20041222-1_i386.deb
dpkg -x dialog_1.0-20041222-1_i386.deb .
export PATH=./usr/bin/:$PATH

However, i get stuck in the second line with ***** - what does he mean by ***? I tried klik.atekon.de and even the whole line but to no avail. And dpkg -x tells me to try 'install' instead... 

could you elaborate? noob here... thanks... love klik!@!!

---

### Post by boltronics on 2005-07-05
Hey Dex,

I wouldn't worry about that. If you're running Hoary, just do:

```
sudo apt-get install dialog xdialog
wget klik.atekon.de/client/install -O -|sh
```

You might need the Hoary Backports [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) mirror in your sources.list file (as mentioned in the [Ubuntu Guide](http://www.ubuntuguide.org/)) for these packages to become available... can't remember.

---

