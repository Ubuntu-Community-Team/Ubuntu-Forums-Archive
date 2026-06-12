---
title: "Pidgin idle time reporting"
date: 2007-06-20
forum: General Help
---

### Post by Face1 on 2007-06-20
Does anybody know if there is a way to get Pidgin (formerly gaim) to report idle times based on X usage, not just last sent message?  In windows you can do it, but I can't figure out any way in ubuntu.

---

### Post by ddhill on 2007-07-19
I am building my pidgin from source and found I was missing a few packages. The latest was the X screensaver extension, and building that in allows for availability based on keyboard and mount.

 sudo apt-get install libxss-dev

I then did a:
  ./configure 
  make
  sudo make install

---

### Post by Face1 on 2007-07-19
Hey yeah, that worked! thanks a lot

---

