---
title: "Problems registering JRE with Firefox"
date: 2007-02-25
forum: General Help
---

### Post by chriswyatt on 2007-02-25
I've just installed the Java Runtime Environment but I'm having trouble registering the plugin with Firefox.  I've been following these installation notes:

[http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")

These are the error messages I get when I execute this line:

sudo ln -s <JRE>/plugin/i386/<ns7 | ns7-gcc29>/libjavaplugin_oji.so

bash: /libjavaplugin_oji.so: Permission denied
bash: ns7: No such file or directory

Am I right in using sudo?  It still won't let me mess with the java plugin :( .  Also, the command used to change the directory didn't work so I had to find the directory myself.

---

### Post by chriswyatt on 2007-02-25
Sorry, ignore this post, I've found instructions through Google.

---

