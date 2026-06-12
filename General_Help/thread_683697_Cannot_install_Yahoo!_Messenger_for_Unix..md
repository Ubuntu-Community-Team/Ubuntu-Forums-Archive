---
title: "Cannot install Yahoo! Messenger for Unix."
date: 2008-01-31
forum: General Help
---

### Post by saptarshi.roy on 2008-01-31
I am facing a weird issue with Yahoo! Messenger for Unix. 
I have downloaded the file ymessenger_1.0.4_1_i386.deb. I double click on the file and the package installer opens and thereafter I get this error message,
" Error: Dependency is not satisfiable: libssl0.9.6."
Alternatively, I open the terminal and type 
sudo dpkg -i ymessenger_1.0.4_1_i386.deb
 but I get this message 
"cannot process archive: No such file or directory."
I would be grateful if someone throws some light on it.
Thanks and regards.
Roy.

---

### Post by jan quark on 2008-01-31
try to install the missing dependency

```

sudo apt-get install libssl0.9.8
```

---

### Post by saptarshi.roy on 2008-01-31
It says libssl0.9.8 is already the newest version.

---

### Post by shrinathk87 on 2008-04-30
Hey even i got the same problem..

i couldnt install yahoo messenger...

but actually my PRIMARY reason for installing yahoo messenger on ubuntu was for its IMVIRONMENTS...and as far as i know, the yahoo messenger for unix DOES NOT HAVE IMVIRONMENTS...so i just left it..

Why dont u try Yahoo messenger with WINE... i am linux newbie and i dont know how to use WINE...so i didnt try it out myself...


tell me how it goes..if possible, teach me how to install it in WINE..

thanks...

---

