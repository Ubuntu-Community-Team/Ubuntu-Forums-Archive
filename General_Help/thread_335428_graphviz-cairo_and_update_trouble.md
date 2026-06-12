---
title: "graphviz-cairo and update trouble"
date: 2007-01-10
forum: General Help
---

### Post by feest on 2007-01-10
hi i've tried to install graphviz cairo but it failed and gave an error, now i can't remove it 

this is the error:
E: graphviz-cairo: subproces post-installation script gaf een foutwaarde 127 terug

in english:
E: graphviz-cairo: returned error 127 to subproces post-installation script
(used translator don't know the exact english output)

how can i remove this also i have a problem updating, i run edgy eft and i can't install certain updates it says i need to do a dist upgrade but that's not possible since i'm already running edge


so i cannot intall linux restricted modules as you can see on the picture

how can i solve those problems

---

### Post by feest on 2007-01-10
*bump*

---

### Post by feest on 2007-01-11
really guys noone who can help

B U M P

---

### Post by maiki_desu on 2007-02-02
I had a similar error.

If I ran
```
sudo apt-get -f install
```
I would get a line that it couldn't finish the post-script install or something.

What I did was:
edit /var/lib/dpkg/info/graphviz-cairo.postinst 
```
goodmami@toshiba:/var/lib/dpkg/info$ sudo vi graphviz-cairo.postinst 
```
Then I took out any lines that would cause something to happen.  In my case, it wanted to install "dot".

then I ran "apt-get -f install" again and it seemed to get rid of the error message.  I don't know if it really fixed the problem or not, but it seemed to work.

---

