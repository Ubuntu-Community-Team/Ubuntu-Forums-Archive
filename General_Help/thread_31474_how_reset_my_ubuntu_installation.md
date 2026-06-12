---
title: "how reset my ubuntu installation"
date: 2005-05-03
forum: General Help
---

### Post by nortoncillo on 2005-05-03
i want to erase all the packages that i aded in the time..
the idea is to reset the ubuntu installation..

thats because i've been playing a lot with many configurations, and i want to organize everithing from the bottom, and that means start from zero

any idea?


----------------
"in a world without any wall or fences
who need windows and gates?"

---

### Post by shakin on 2005-05-03
If you've installed with Synaptic you can go to its history to see which packages were installed on which day and go backwards from there. You can also run 'dpkg-reconfigure {packagename}' to have Ubuntu reconfigure the package if the configuration has been corrupted.

---

### Post by nortoncillo on 2005-05-03
my idea is to do it from the console.. .

because i use ssh conections, and run a vncserver would be too slow... 

i've been trying with # apt-get remove {package}

and it's working, but it's too damn slow...

is there some kind of # rm -rf all-packages

hehe

---

### Post by az on 2005-05-03
You can use aptitude....
sudo aptitude

---

