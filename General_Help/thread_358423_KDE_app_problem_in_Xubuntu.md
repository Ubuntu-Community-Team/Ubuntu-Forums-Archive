---
title: "KDE app problem in Xubuntu"
date: 2007-02-10
forum: General Help
---

### Post by toran on 2007-02-10
I have a fairly new xubuntu install, and I recently tried to install
amarok from the kubuntu amarok repository.

I added the amarok repositories to my apt sources.list and ran "sudo
aptitude install amarok". It went about installing all dependencies.
When it finished, I tried to run amarok, but it crashed with the
following error:

Floating point exception (core dumped)

further investigation shows a crash when trying to start kdeinit:

jon@gimli:~$ kdeinit
Creating link /home/jon/.kde/socket-gimli.
Created link from "/home/jon/.kde/socket-gimli" to "/tmp/ksocket-jon"
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/jon/.DCOPserver_gimli__0
and start dcopserver again.
---------------------------------

Creating link /home/jon/.kde/tmp-gimli.
Created link from "/home/jon/.kde/tmp-gimli" to "/tmp/kde-jon"
kded: ERROR: Communication problem with kded, it probably crashed.
jon@gimli:~$

I actually tried installing kubuntu-desktop and logging into KDE. When
logged into kde, amarok actually ran. Logging back into XFCE, it
crashed. What's going on?

I also checked and have kdebase-kio-plugins installed, so that is not the problem.

Further investigation shows that this problem extends to all KDE applications. Someone please help.

---

### Post by kerry_s on 2007-02-10
Did you launch kde services on startup? (menu>settings>sessions&startup>advanced)

---

### Post by toran on 2007-02-11
Yes. It didn't change anything.

---

