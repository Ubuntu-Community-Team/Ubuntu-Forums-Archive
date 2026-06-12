---
title: "please help me install the sources for your kernel image"
date: 2007-10-03
forum: General Help
---

### Post by Christ_Guard on 2007-10-03
hi guys,
   I am trying to install some drivers and have been informed that I need to install the sources for my kernel image. What does this mean and how do I do it? Thanks! P.S. I am running Ubuntu FF on a toshiba tecra laptop.

-Christ_Guard

---

### Post by wirelessmonkey on 2007-10-03
sudo apt-get install linux-headers

---

### Post by Christ_Guard on 2007-10-03
I run that and it gives me a list of linux-headers and says "You should explicitly select one to install: and "E. Package Linux-headers has no installation candidate"

-Christ-guard

---

### Post by distroman on 2007-10-03
```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by bodhi.zazen on 2007-10-03
```
sudo apt-get install linux-headers-`uname -r`
```

Note those are bac tics, by the number 1 and not single quotes

bac tic `
quote '

---

### Post by Christ_Guard on 2007-10-04
Only problem is now that I dont have the internet, my wireless drivers are what I am trying to install and need this for so this allways get hung at "Connecting to security.ubuntu.com" or whatever. Any way around this?

---

### Post by bodhi.zazen on 2007-10-04
Aptoncd: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

