---
title: "can't chown /var/log/messages"
date: 2004-12-02
forum: General Help
---

### Post by ubuntu_demon on 2004-12-02
Hi,

apt-get has a problem :

Setting up sysklogd (1.4.1-16ubuntu4) ...
 * Stopping system log daemon...                                         [ ok ]
chown: changing ownership of `/var/log/messages': Operation not permitted


======

messages has the following permissions :
-rw-r--r-- 1 root root 1080425 2004-11-29 17:41 messages


lsattr gives :

-----a----------- messages

I can't remove or chmod or chown the file.

anyone ?

(see also : [http://www.ubuntuforums.org/showthread.php?p=27435#post27435](http://www.ubuntuforums.org/showthread.php?p=27435#post27435))

---

### Post by ubuntu_demon on 2004-12-02
I thought the "a" attribute couldn't be it (append only) but it was :). 

solved!

---

