---
title: "Dependancy problems"
date: 2005-05-14
forum: General Help
---

### Post by Kurai on 2005-05-14
i am havig a problem w/ ndiswrapper there's what's happening:
I go to the root terminal switch to /usr/src and enter
```
dpkg -i ndiswrapper.deb
``` 
Then it tells me:
```
dpkg dependancy problem.
package gcc is not installed
dependancy problem - leaving unconfigured
``` 
Does anyone know how I can fix this I have installed altgcc _2.7.2.3-2_i386.deb and i still get the same error.  Any suggestions?

---

### Post by tread on 2005-05-14
sudo apt-get install build-essential

---

### Post by Kurai on 2005-05-14
now it's telling me
```
Dependancy problems
package module-assistant not installed
```
Edit:  I tried "sudo apt-get install module-assistant" and it told me it doesn't exist

---

### Post by Knome_fan on 2005-05-14
I think you need to enable the universe repository.
Put the following into /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

run sudo apt-get update and you should find the package.

I don't have any experience with ndiswrapper, but there are also two ndiswrapper packages in universe:
 ndiswrapper-utils - Userspace utilities for ndiswrapper
ndiswrapper-source - Source for the ndiswrapper linux kernel module

Hope this helps.

---

