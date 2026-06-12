---
title: "Local Debian Universe (or finding Opera)"
date: 2004-10-26
forum: General Help
---

### Post by steffen on 2004-10-26
I am not able to find Opera (my preferred browser on any platform) in the Ubuntu repository, Debian Universe, restricted repository or the multiverse.

However, I am able to download a .deb file from opera.com for Debian Sid (3.1), which I haven't figured out how to install.

Does anyone know (of course, but I'm putting it in question form anyway 8) ) how to install a single piece of .deb software. or alternatively how to make a local debian repository.

I found some instructions on debian.org on how to set up a local repository, but I didn't understand it...  :???:

---

### Post by castrojo on 2004-10-26
sudo dpkg -i whatever.deb should do the trick.

---

### Post by steffen on 2004-10-26
Seems it did :)

For anyone else (newbies :???: ) attempting to install Opera - install QT libraries first...

---

### Post by jdong on 2004-10-26
Opera has an APT repository: **deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free **

---

