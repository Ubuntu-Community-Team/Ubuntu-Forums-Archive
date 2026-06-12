---
title: "Java+Firefox = Not working"
date: 2005-08-08
forum: General Help
---

### Post by BanskuZ on 2005-08-08
My Java doesn't work. I will get "Additional plugins are required to display all media on this page" msg.
[[IMG]http://img334.imageshack.us/img334/3439/javadoesntwork0uw.th.png[/IMG]](http://img334.imageshack.us/my.php?image=javadoesntwork0uw.png)
I installed java with [this guide](http://www.ubuntuguide.org/#jre).

---

### Post by ujin on 2005-08-08
[QUOTE=BanskuZ]My Java doesn't work. I will get "Additional plugins are required to display all media on this page" msg.
[[IMG]http://img334.imageshack.us/img334/3439/javadoesntwork0uw.th.png[/IMG]](http://img334.imageshack.us/my.php?image=javadoesntwork0uw.png)
I installed java with [this guide](http://www.ubuntuguide.org/#jre).[/QUOTE]


im under debian but it should be ok for ubutus  . Its a "do it by yourself" step by step  .


making java progs working . i wonder why windows has a gui as installer   grrrrr


download the java jvm from java ,take Linux (self-extracting file)
save the file in your home folder.

1)open a terminal log as root  type "sudo su"
2) type "chmod +x  jre-1_5_0_04-linux-i586.bin"
3)type "cp -f jre-1_5_0_04-linux-i586.bin  /usr"
4)type "cd /usr"
5)type "./jre-1_5_0_04-linux-i586.bin"
6)type "rm -f jre-1_5_0_04-linux-i586.bin" (dont need it anymore so we can delete)
7)type "cd jre-1_5_0_04-linux-i586"
8)type "cd bin"
9)(delete old java link if any) rm -f /usr/src/java
10) make a simlink  to the default system searchpath  type "ln -s /usr/jre1.5.0_04/bin/java /usr/bin/java"

firefox's turn 

i've installed firefox on my home directory 
/home/ujin/sys/firefox-installer
what u have to do to make firefox working with java is to build a simlink to the firefox plugin folder . that's all 

type "ln -s /usr/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so    /home/ujin/sys/firefox-installer/plugins/libjavaplugin_oji.so " 

and voila java is working with firefox (maybe )   \\:D/ 
java works better with konqueror dunno why 

Ciao

---

### Post by BanskuZ on 2005-08-09
**THANK YOU!**
Now my Java works.

---

### Post by fng on 2005-08-10
Or you could follow the easy way :)
[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

---

