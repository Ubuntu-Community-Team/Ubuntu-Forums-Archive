---
title: "Frostwire and Firewall problem"
date: 2008-01-30
forum: General Help
---

### Post by 565Customz on 2008-01-30
hey guys. i have searched this and i found a couple of threads on it but no solution. i run gutsy and icedtea 1.7.

problem:
frostwire will not connect (says its because its behind a firewall. but i have none setup...not even firestarter.

when i go to applications and go to jave webstart icon i get this message...(which leads me to beleive its a java problem.)
                     

                                     Failed to execute child process 

"/usr/lib/jvm/java-7-icedtea/bin/javaws" (No such file or directory)

---

### Post by taurus on 2008-01-30
There is a default firewall, iptables, which starts at boot.  If you need to open a port for frostwire, you may want to install firestarter and use it to configure your firewall.  Again, firestarter is NOT the firewall; it is just a GUI app to configure firewall, iptables.

---

### Post by 565Customz on 2008-01-31
man frostwire is garbage.....now it runs the seup everytime it opens....and half the time it wont even open. and it wont connect even with the port number changed....wtf

---

### Post by tarreaga on 2008-02-24
I have a 2Wire Router.  Found a fix online.  Did not have to forward a port or change any Frostwire settings.  Go to this site [http://www.mybloop.com/FTA/fixconnecting.zip](http://www.mybloop.com/FTA/fixconnecting.zip).  Download and install than restart Frostwire.  Worked for me.

---

### Post by cbiere on 2008-02-25
Your URL points to a ZIP-packed executable for Windows XP. How this going to help anyone with a Linux-based operating system like Ubuntu? Even if it would work who in his right mind would download and execute some dubious program from an unknown website? Who says this doesn't contain a virus or applies some dangerous modification to FrostWire? I find it quite interesting that you bothered to sign up just to link to this file but didn't even take the time to think about in what kind of forum you are posting.

---

