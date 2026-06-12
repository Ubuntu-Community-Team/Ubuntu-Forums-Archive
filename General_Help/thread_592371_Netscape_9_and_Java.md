---
title: "Netscape 9 and Java"
date: 2007-10-26
forum: General Help
---

### Post by alligoodw on 2007-10-26
I've installed Netscape Navigator 9 on my Ubuntu 7.10 distro.  With a single exception it works flawlessly.  What is the exception?  Java doesn't work and I'm not sure how to manually put the gears into action here.  Is there anyone who has a solution?

---

### Post by manuquadros on 2007-11-10
I managed to make it work. What I did was going to my netscape's plugin path, which in my case was /usr/bin/navigator/plugins, and created a symbolic link to libjavaplugin_oji.so, using:

[INDENT]sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so
[/INDENT]

I guess the name and path of your plugin may vary, depending on its version. Mine is 1.6.0.03-b05.

---

