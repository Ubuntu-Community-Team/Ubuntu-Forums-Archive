---
title: "Uninstall programs?"
date: 2008-05-09
forum: General Help
---

### Post by DeKosta on 2008-05-09
Hello
I could start with telling you that im new to linux so bear with me.
Lets say i install a program through the terminal with ./configure, make and install.
How can i uninstall the same program when i dont want it anymore?

This far i have uninstalled stuff through synaptic manager, but that is only avalible if the program is found in the manager right..

Thanks!

---

### Post by Monicker on 2008-05-09
make uninstall

---

### Post by Zorael on 2008-05-09
Usually, much like you do **make install**, you can do **make uninstall**.

As you said, Synaptic/Adept etc are package managers, and if what you installed didn't come in a .deb package they aren't keeping track of it.

---

### Post by Perfect Storm on 2008-05-09
and ofcause this shall be done in the source code of the application/lib/whatever-you-compiled directory.
If you used sudo make install, you should as well do sudo make uninstall.

---

### Post by DeKosta on 2008-05-09
Thanks for yout replies guys!

---

