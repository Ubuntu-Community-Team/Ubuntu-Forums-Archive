---
title: "Dpkg broken x..x"
date: 2007-06-20
forum: General Help
---

### Post by Flying George on 2007-06-20
I was recently trying to install pidgin on Ubuntu 6.10, I needed GTK+ to install pidgin, and for GTK+ I needed cairo. I sudo aptitude installed cairo, it came back with about twenty results, I installed them all. One of these packages seems to have broken my dpkg. The package in question: graphviz-cairo. I installed that, it failed and now every time I try to install something via terminal or synaptic, it fails. How can I fix this? (Preferably *without* re-installing.)

---

### Post by Happy_Man on 2007-06-20
Can you still remove stuff? Have you tried removing this offending package?

---

### Post by Flying George on 2007-06-20
Yes, I have tried via command line

sudo apt-get remove graphviz-cairo

however that did not work. I'll try once more through synaptic.

Tried removing through synaptic:

[[IMG]http://img516.imageshack.us/img516/6974/screenshotzi2.th.png[/IMG]](http://img516.imageshack.us/my.php?image=screenshotzi2.png)

---

### Post by Happy_Man on 2007-06-20
Were you using the .deb from [http://getdebs.net?](http://getdebs.net?) From what I can tell, you seem to be trying to compile it.... compiling is a pain in the ***. Use debs. Debs are god.

---

### Post by Flying George on 2007-06-20
I wasn't trying to compile graphviz-cairo, the only thing I was compiling was GTK+ and pidgin, that was all pretty usual.

./configure
make
sudo make install

That's not the problem...the dependency just won't install or un-install...i'm at my whits end.

---

