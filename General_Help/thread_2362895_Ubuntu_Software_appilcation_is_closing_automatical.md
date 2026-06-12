---
title: "Ubuntu Software appilcation is closing automatically"
date: 2017-06-03
forum: General Help
---

### Post by ashikta2001 on 2017-06-03
Dear team,

I'm facing an issue in Ubuntu 16.04 LTS. when I try to open the Ubuntu Software to install any applications the window is opening and closing automatically.

please provide a solution for the same.

thanks 

Ashik

---

### Post by leunam12 on 2017-06-03
Did you try purging and re-installing? ```
sudo apt remove --purge software-center
sudo apt update
sudo apt install software-center
```

---

### Post by Impavidus on 2017-06-03
Maybe it encountered an inconsistency in the package database. It shouldn't happen, but sometimes it does. Try```
sudo apt update
sudo apt upgrade
```Any error messages?

Ubuntu Software is friendly to beginners, but as usual that comes with the downside of being not very capable.

---

### Post by arkmundi on 2017-06-04
I had the same issue.  After upgrading to LTS 16.04, the menu icon would animate as if attempting to load, but failed to launch.  I completed removed & purged the app, then installed software-center as suggested.  When I use the menu search icon, I now notice that there are two identical icons for the app, the first of which acts as above.  The second icon succeeds in launching it.  Since before, I had software-center locked to the launcher, I suspect it simply remained in place, pointing to a null package.  I unlocked it, used search and selected the second icon listing, locked that to the launcher and all is well.  There is something funking going on, but I'm good now.

---

