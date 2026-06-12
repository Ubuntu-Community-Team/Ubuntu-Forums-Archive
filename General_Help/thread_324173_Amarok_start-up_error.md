---
title: "Amarok start-up error"
date: 2006-12-23
forum: General Help
---

### Post by GeeBee on 2006-12-23
Hello to all,

Some help please with the following. I know being a (not absolute) beginner I should not have started off with Edgy, but every thing was working fine, except for the following message when I tried to start Amarok:

Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

It was working before. Could someone translate the above in human please, thnx!

---

### Post by PriceChild on 2006-12-23
```
sudo apt-get amarok amarok-xine
```

---

### Post by GeeBee on 2006-12-23
Thanks, but it does not help. Terminal replies 'invalid operation amarok' (translation). I tried it both with Amarok installed and after completely removing it with Synaptic, both resulted in above.

---

### Post by PriceChild on 2006-12-23
whoops sorry my mistake...
```
sudo apt-get install amarok amarok-xine
```

---

### Post by GeeBee on 2006-12-24
Same problem, by the looks of it Amarok and Xine are installed just fine, but when I start up Amarok I still get the error and Amarok does not start up. I remember that the problem started after an update of, amongst others, OpenOffice.

---

### Post by DarkDead on 2006-12-27
Hi. I get the same error but in a new installation. I've never used Amarok before and when I installed it I get the error reported by GeeBee a other two before:
First error: 
There was a error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.

/home/david/.DCOPserver_PRINCIPAL__0

Please check that the "dcopserver" program is running!

Second error:
Malformed URL
file:///


Any idea?

---

