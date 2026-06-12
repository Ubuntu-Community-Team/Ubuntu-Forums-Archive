---
title: "Help downloading Swiftfox"
date: 2007-12-10
forum: General Help
---

### Post by justinclark on 2007-12-10
I tried using the installer instructions on the site but the terminal says sh. cant open the file.  How do I just download the darn thing?

---

### Post by edm1 on 2007-12-10
1) Open a terminal (Applications>Accessories>Terminal)
```
gksudo gedit /etc/apt/sources.list 
```
which opens the file '/etc/apt/spurces.list' using gedit.

2) Add this

```
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

```
to the end of the document and save.

3)
```
sudo apt-get update
```
which will update the list of packages.

4) Swiftfox will now be available using synaptic (System>Admin>Synaptic Package manager). You'll need to know your processor type.

---

### Post by justinclark on 2007-12-10
Sorry Im such a noob, save that to the end of what file?  Thanks

---

### Post by edm1 on 2007-12-10
sorry, i've made it clearer now, hopefully.

---

### Post by justinclark on 2007-12-10
It worked thanks a lot!

---

