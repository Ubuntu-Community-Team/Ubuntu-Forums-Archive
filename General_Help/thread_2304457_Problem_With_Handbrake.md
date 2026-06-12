---
title: "Problem With Handbrake"
date: 2015-11-26
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-26
I'm trying to copy my DVD's to my HDD and Handbrake is not working since upgrading to Ubuntu 15.10.  I start Handbrake, put in the DVD, press Source, then press Detected dvd devices - /dev/sr0, it goes through the process of reading the dvd, but after it's done the Start button never highlights!  Anyone know what's wrong?

---

### Post by cariboo on 2015-11-26
Click the Activity button, and show us what the output is, I suspect you haven't got libdvdcss installed. Things have changed in versions newer than 15.10, you now have to install libdvd-pkg, which is in the repositories.

---

### Post by shane_faulkinbury2 on 2015-11-26
Well I downloaded libdvdcss.pkg and libdvdcss.2.dylib and the following pic is what I get when I click on them!  There is also a pic of the Activity on Handbrake.  What am I supposed to do from here?

---

### Post by cariboo on 2015-11-26
After installing libdvd-pkg you need to run:

```
sudo dpkg-reconfigure libdvd-pkg
```

to install the library.

---

### Post by shane_faulkinbury2 on 2015-11-27
But how do I install it?  This is what I get so far!

Nevermind!  I got it all figured out and DVDs are coping fine now! :p

---

