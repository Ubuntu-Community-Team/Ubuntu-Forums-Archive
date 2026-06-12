---
title: "Problems installing JRE in Konsole"
date: 2008-04-29
forum: General Help
---

### Post by 09amw on 2008-04-29
Hi -- I'm trying to install Sun's version of the Java6 Runtime Environment, so I tried to install using aptitude in the terminal, as one would assume:

sudo apt-get install sun-java6-jre sun-java6-plugin

However, when aptitude gets around to installing these packages, it brings up a GUI interface to agree to the EULA -- and I can't accept it.  I'm now trapped in the vicious cycle of not being able to install the JRE because I can't accept the EULA, and not being able to stall anything else, because I have a hanging installation.

How can I fix this?  Either by figuring out how to accept the EULA or cancel the installation entirely so that I may do it entirely graphically.

Thanks for the help!

---

### Post by DMK62 on 2008-04-29
I have always used Adept or Synaptic to install Java but the following should apply as the eula part is also messed up with those methods.

Try hitting Enter several times until it comes to the end of the eula and enter Y to agree.

If that does not work have to tried scrolling with your keyboard or used Page Down ?

Dale

---

### Post by 09amw on 2008-04-29
I had to use the side arrow keys to eventually select the <Ok> dialogue.  Thanks for the help!

---

