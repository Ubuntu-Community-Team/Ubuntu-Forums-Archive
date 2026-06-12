---
title: "Weird  azureus cpu usage."
date: 2007-02-25
forum: General Help
---

### Post by cooldudevamsee on 2007-02-25
Hi,

I installed azureus using apt-get. Since then azureus has singnificant amount of cpu usage (over 60%.

This is my updata-alternatives output

vamsee@vamsee-desktop:~/ss2$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java


vamsee@vamsee-desktop:~/ss2$ dpkg -l | grep azureus
ii  azureus                                    2.5.0.0-0ubuntu2                     BitTorrent client



And if I use sun-java5-jre from ubuntu ports to run azureus then azureus is core dumping.

Ss there any specifc version of azureus that can fix this problem ?

---

### Post by nrune on 2007-02-25
I have not noticed these issues, I installed Azureus with Automatix.  Of other consideration is Deluge. Lightweight torrent manager aval in edgy synaptic. 

Have FUN

---

### Post by cooldudevamsee on 2007-02-26
K, Then I will try with automatix, and will post what happened.

---

