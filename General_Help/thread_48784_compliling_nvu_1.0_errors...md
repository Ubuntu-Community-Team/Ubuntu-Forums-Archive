---
title: "compliling nvu 1.0 errors.."
date: 2005-07-13
forum: General Help
---

### Post by darknight on 2005-07-13
am trying 2 compiling nvu 1.0 i av sorted most of the dependencies but can't work this 1 out, i know i can get nvu 0.99 from apt but wud rather av 1.0 configure: error:  Could not find the following X libraries:  -lXt

---

### Post by AAUU on 2006-01-17
You need the header files for xt.  It should be something like libxt-dev in synaptic.  Or just do a 

apt-get install libxt-dev

---

