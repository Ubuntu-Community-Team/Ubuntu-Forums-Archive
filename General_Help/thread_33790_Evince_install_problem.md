---
title: "Evince install problem"
date: 2005-05-12
forum: General Help
---

### Post by Nissemand on 2005-05-12
I'm pretty new to Linux, and not pretty sure on how to solve the problems i get. So i figure out that the best way to learn, is to ask (and search google  :) ).
I just installed Ubuntu, and now I'm trying to install Evince 0.2.1. But when I do ./configure, first it looks normal, but then in the end it tells me:

[B]checking for gtk+-2.0 >= 2.4.0 libgnomeui-2.0 >= 2.4.0... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 2.4.0 libgnomeui-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.[/B] 

I hope people in here will help a poor beginner like me.

---

### Post by qstone on 2005-05-12
Don't be ashame to be a "poor beginner", everyone of us was, or still is, a beginner  ;-) 
Use the easy way to install evince : it's in the repositories (universe, maybe ? If you don't know what it is, or how to do, check [www.ubuntuguide.org](www.ubuntuguide.org), they explain the whole thing). Look for "evince" in synaptic, or sudo apt-get install synaptic form a terminal...

---

### Post by mrtaber on 2005-05-12
Yup, I found it using Synaptic.  A nice package.

Mark :)

---

### Post by Nissemand on 2005-05-12
wow great guide :D thank you a lot

---

