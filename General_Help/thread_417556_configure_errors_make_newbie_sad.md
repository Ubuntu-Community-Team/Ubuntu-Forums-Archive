---
title: "configure errors make newbie sad"
date: 2007-04-21
forum: General Help
---

### Post by tiana on 2007-04-21
I tried to install something recently and I got the following configure error:

checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 glib-2.0 libgnomeui-2.0 libglade-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found

configure: error: Library requirements (gtk+-2.0 glib-2.0 libgnomeui-2.0 libglade-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I get something similar to this with different requirements not met with just about anything I try to install!  What's a girl to do???:confused:

---

### Post by mhansen on 2007-04-21
What command are you using to try to install these packages?

---

### Post by tiana on 2007-04-21
I am using kconfigure to install it

---

### Post by mhansen on 2007-04-21
Save yourself the trouble and use apt, which handles dependencies for you.  

Open up a console and type sudo apt-get update, then sudo apt-get install <package>.  whatever you're missing will be installed as well.  AND, it'll automatically get added to your KDE menu (at least everything I've installed has) for you, if that was your concern.


Regards,
Mike

---

