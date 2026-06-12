---
title: "some bug with Opera Browser after i installed Breezy"
date: 2005-10-14
forum: General Help
---

### Post by piparkuka on 2005-10-14
After Breezy installation i got some new bug on Opera opening

it shows me the window with the message:
-------------------------------------
Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.
Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/opera/plugins/operamotifwrapper-3
Please install Motif.
Plug-in path
(Path can be modified in Preferences dialog)
/usr/lib/opera/plugins
---------------------------------------

The installation of Opera was succefull. I allready installed java and flash plugins and i'd like to undestand what it's talking about.
i have to say that before breezy when i used hoary i didn't have such problem.

10x

---

### Post by majikstreet on 2005-10-14
Look in the Breezy how-to's section. There is a how-to there about making the plugins in Opera work.

I am in Opera right now, it's nice.:p

---

### Post by Lambert on 2005-10-14
If you installed the ubuntu version you will probably have problems with this as I did. I uninstalled that version and installed the static.deb version.

Either way you will need to install lesstif.

The browser will work, you will just have problems with plugins. 

you can do a search in this forum or in google using the error line you get and you'll find many have had this problem. Read their threads and you will find an answer.

Found this thread a minute later. [http://www.ubuntuforums.org/showthread.php?t=76236](http://www.ubuntuforums.org/showthread.php?t=76236)

---

### Post by piparkuka on 2005-10-15
i'm sorry

but it didn't really helped me.
i still have the same problem

i allready tryed to install motif-clients, put original motif from opera.tar.gz to plugins directory
And still the on opening i get this error

may be it will help you, friends

igor@ubuntu:~$ opera -debugplugin
opera: [plugin probing] /usr/lib/opera/plugins/libflashplayer.so
opera: [plugin probing] /usr/lib/opera/plugins/libnpp.so
opera: [plugin path   ] #001: /usr/lib/opera/plugins
opera: Search operamotifwrapper: [No] /usr/lib/opera/plugins/operamotifwrapper
opera: Search operamotifwrapper: [No] /usr/lib/opera/plugins/operamotifwrapper-1
opera: Search operamotifwrapper: [No] /usr/lib/opera/plugins/operamotifwrapper-2
opera: Search operamotifwrapper: [No] /usr/lib/opera/plugins/operamotifwrapper-3

igor@ubuntu:~$ ls -al /usr/lib/opera/plugins
total 168
drwxr-xr-x  2 root root  4096 2005-10-16 02:53 .
drwxr-xr-x  4 root root  4096 2005-10-14 03:44 ..
lrwxrwxrwx  1 root root    41 2005-10-14 03:51 flashplayer.xpt -> /usr/lib/macromedia-flash/flashplayer.xpt
lrwxrwxrwx  1 root root    43 2005-10-14 03:51 libflashplayer.so -> /usr/lib/macromedia-flash/libflashplayer.so
-rw-r--r--  1 root root 66528 2005-09-16 13:14 libnpp.so
-rwxr-xr-x  1 igor igor 77520 2005-09-16 13:14 operamotifwrapper-3
-rwxr-xr-x  1 root root  6944 2005-09-16 13:14 operaplugincleaner

---

### Post by grangouze on 2005-10-19
See [http://perso.normandnet.fr/gamianol/travaux/toshiba/index.html#Ubuntu](http://perso.normandnet.fr/gamianol/travaux/toshiba/index.html#Ubuntu)

---

