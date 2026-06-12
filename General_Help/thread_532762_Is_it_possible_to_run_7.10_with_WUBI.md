---
title: "Is it possible to run 7.10 with WUBI???"
date: 2007-08-23
forum: General Help
---

### Post by sreejithr on 2007-08-23
That would be great so anyone who has done it please tell me...if there is anything extra to do please tell me also...

---

### Post by ago on 2007-08-23
Not yet. There will be some alpha releases for devs relatively soons, but at the moment there are bugs that prevent it from booting and some parts are not implemented

---

### Post by sreejithr on 2007-08-23
tks

---

### Post by tuxcantfly on 2007-08-23
As ago said, the loopmounting code for Ubuntu 7.10 isn't done yet, but if all you need is the no-cd install features, and you want a regular install not a loop-install, you could use UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) since it supports Ubuntu 7.10

---

### Post by sreejithr on 2007-08-24
is unebootin safe??? is it same as wubi or what is  the differnce...could u give me details on what it does??? u c my problem is that I tried installing ubuntu with a CD but i never managed to partition it....what does this do???

---

### Post by tuxcantfly on 2007-08-24
> is unebootin safe??? is it same as wubi or what is the differnce...could u give me details on what it does??? u c my problem is that I tried installing ubuntu with a CD but i never managed to partition it....what does this do???

It's different, as in Wubi installs to a loopmounted partition and UNetbootin installs to a real one, like the official Ubuntu does. It should be just about as safe, since the NTFS resizing code in Ubuntu has improved a lot and is now very reliable (though you might want to back up important data just in case). Essentially, it's identical to the standard installation process, only no CD is required; it downloads the installation files on the go from the internet while installing.

---

