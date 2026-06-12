---
title: "JRE Install help"
date: 2007-12-03
forum: General Help
---

### Post by Headcrab on 2007-12-03
Hi there, Im trying to get jre installed on my x64 Xubuntu so I can use frostwire

But.... well.... Ill let the image do the talking

[[IMG]http://img222.imageshack.us/img222/6986/23288042gz2.jpg[/IMG]](http://imageshack.us)

---

### Post by PeterJS on 2007-12-03
Try enabling the universe and multiverse repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Chen Jun on 2007-12-03
Here is what I did:

1. download the JRE package (jre-6u3-linux-i586.bin) from Sun web site.
2. chmod u+x jre-6u3-linux-i586.bin
3. cd /opt (you may install it to other directory you like)
4. sudo /<path>/jre-6u3-linux-i586.bin

after install
# cd <your home directory>
# cd .mozilla/plugins
# ln -s /opt/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

---

