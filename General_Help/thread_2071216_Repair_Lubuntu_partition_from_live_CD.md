---
title: "Repair Lubuntu partition from live CD?"
date: 2012-10-14
forum: General Help
---

### Post by SteveDeFacto on 2012-10-14
I installed Thunar and liked it so I decided to make it my default file manager. I removed Pcmanfm thinking it would make lubuntu change the file manager to Thunar. It didn't work so I decided to restart but after that the system would no longer boot. I'm using a live CD of lubuntu and I can access the drive but I have no idea how to reinstall pcmanfm from a live CD. How do I fix it from here?

---

### Post by Kirk Schnable on 2012-10-14
I would think you would still be able to get to the TTY... 

Try booting off the hard drive, but when you get to the furthest point in the boot process that it's getting to, press CTRL+ALT+F1.  

Unless you've done some serious damage, this should give you a login prompt.  Type your username\password, and you'll be given a terminal shell.  Now you should be able to use sudo apt-get install as normal.

Kirk

---

### Post by SteveDeFacto on 2012-10-15
> **Kirk Schnable said:**
> I would think you would still be able to get to the TTY... 

Try booting off the hard drive, but when you get to the furthest point in the boot process that it's getting to, press CTRL+ALT+F1.  

Unless you've done some serious damage, this should give you a login prompt.  Type your username\password, and you'll be given a terminal shell.  Now you should be able to use sudo apt-get install as normal.

Kirk

It worked! I was not aware of CTRL+ALT+F1. Thank you!

---

### Post by Kirk Schnable on 2012-10-17
> **SteveDeFacto said:**
> It worked! I was not aware of CTRL+ALT+F1. Thank you!

No problem, glad you got it working!  Please mark this thread as solved...

Kirk

---

