---
title: "No Included Compiler?"
date: 2004-10-28
forum: General Help
---

### Post by Conquerer on 2004-10-28
I just recently installed Ubuntu, and although I find it to be excellent, there doesn't seem to be any built in C/C++ compiler. And of course,all the compilers need to be compiled to be installed... Short of installing a binary, is there any other way to compile source? Thanks in advance.

-Conquerer

---

### Post by mark on 2004-10-28
[QUOTE=Conquerer]I just recently installed Ubuntu, and although I find it to be excellent, there doesn't seem to be any built in C/C++ compiler. And of course,all the compilers need to be compiled to be installed... Short of installing a binary, is there any other way to compile source? Thanks in advance.

-Conquerer[/QUOTE]Here's a link to the Ubuntu FAQ that might help: 
[http://www.ubuntulinux.org/support/documentation/faq/development](http://www.ubuntulinux.org/support/documentation/faq/development)

---

### Post by Conquerer on 2004-10-28
Thanks, that did help, but how do I install the "build-essential" package?

---

### Post by flygmaskin on 2004-10-28
[QUOTE=Conquerer]Thanks, that did help, but how do I install the "build-essential" package?[/QUOTE]
 ```
 $ sudo apt-get install build-essential
```
should do the trick

---

### Post by sr.pato on 2004-10-28
[QUOTE=flygmaskin]```
 $ sudo apt-get install build-essential
```
should do the trick[/QUOTE]

When I type in this code I get a message that the system can not find the build-essential package. The message is 'no such file or directory' I get this message with or without the cd mounted. Do I need to be in a sepcific directory to makes this work?

Regards,
Duck

---

### Post by Conquerer on 2004-10-28
Thanks.

---

